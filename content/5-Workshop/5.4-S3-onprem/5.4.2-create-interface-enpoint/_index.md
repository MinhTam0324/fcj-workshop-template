---
title: "Live Captioning – Transcribe & Translate in Action"
date: 2026-07-08
weight: 2
chapter: false
pre: " <b> 5.4.2. </b> "
---


## How the Real-Time Pipeline Works

When a user clicks **Start**, the following chain of events happens automatically:

```
Browser microphone
  → Web Audio API worklet (16 kHz resampling)
  → Binary PCM chunks sent over WebSocket (WSS)
  → CloudFront /ws/transcribe
  → Application Load Balancer
  → FastAPI on ECS Fargate (port 8000)
  → Amazon Transcribe Streaming (two parallel streams: vi-VN and en-US)
  → Amazon Translate (finalized segments only)
  → Caption rows returned over the same WebSocket path
  → Browser caption dashboard
```

The microphone only starts capturing audio **after** the backend health check
passes and the WebSocket connection is established. Audio produced while the
socket is not open is dropped rather than buffered.

## Bilingual Dual-Stream Mode

With `BILINGUAL_DUAL_STREAM=true`, the backend fans each PCM chunk into two
parallel Amazon Transcribe streams:

1. **`vi-VN`** – detects Vietnamese speech
2. **`en-US`** – detects English speech

An arbitrator picks the language that produced the finalized segment first, then
sends that text to Amazon Translate to produce the other language. The result is
a bilingual row:

```
[Vietnamese original]  |  [English translation]
[English original]     |  [Vietnamese translation]
```

Only **finalized** segments become permanent caption rows. Partial (interim)
results may appear in the UI transiently but are never stored.

## Connection Resilience

| Event | Behaviour |
|---|---|
| Normal operation | Frontend sends `ping` every 30 seconds; backend replies `pong` |
| Unexpected disconnect | Frontend retries up to 3 times: 1 s, 2 s, 4 s backoff |
| Reconnect success | New backend session starts; finalized rows are preserved in UI |
| All retries fail | Audio capture stops; user must press Start again |
| 30-minute timeout | Backend closes session; frontend shows "Session ended" |

## Session Guardrails

The backend rejects new connections when limits are exceeded:

- **4 concurrent sessions** globally (one ECS task, process memory)
- **1 session per client IP**

These limits prevent accidental runaway Transcribe/Translate costs for the MVP.
Before scaling beyond one task, the session registry must move to DynamoDB or
Redis (shared state across tasks).

## Start a Live Session

1. Open `https://dpeohr327wt9l.cloudfront.net`
2. Click **Start captioning** to go to `/app`
3. Click **Start** – the frontend wakes the backend if needed, then polls health
4. Allow microphone access when prompted by the browser
5. Speak in English or Vietnamese
6. Watch finalized bilingual caption rows appear in the dashboard:

![LiveCap caption dashboard showing bilingual caption rows](/images/3-Project/livecap-dashboard.png)

The production dashboard ready to start a session:

![Production dashboard showing session controls and status before start](/images/5-Workshop/livecap-production-dashboard-ready.png)

## What If Microphone Access Is Denied?

If the browser blocks microphone access, LiveCap stops before opening any
stream and shows an actionable error instead of leaving a broken session open:

![Frontend showing microphone permission required error state](/images/5-Workshop/livecap-microphone-permission-required.png)

In this case, allow microphone access in the browser site settings and reload
`/app`.