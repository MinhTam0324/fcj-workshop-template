---
title: "End-to-End Verification"
date: 2026-07-08
weight: 4
chapter: false
pre: " <b> 5.4.4. </b> "
---

This step confirms that the entire LiveCap stack – from browser to CloudFront,
ALB, Fargate, Transcribe, Translate, and back – is working correctly together.

## Verification Checklist

Run through this checklist in order. Each step builds on the previous one.

### 1. Health Endpoint

```powershell
Invoke-RestMethod https://dpeohr327wt9l.cloudfront.net/api/health
```

Expected: `{"status": "healthy", "version": "1.0.0"}`

If this fails, the ECS task is not healthy or CloudFront routing is broken.
Check the ALB target group health status first.

### 2. Backend Reachable via CloudFront

The health endpoint goes through the full CloudFront → ALB → Fargate path.
A `200 OK` response confirms:

- CloudFront distribution is deployed and accepting requests ✓
- ALB listener is routing to the ECS target group ✓
- ECS Fargate task is healthy and responding on port 8000 ✓

### 3. WebSocket Connection

Open your browser's developer tools (F12) → Network tab → filter by WS.
Then click **Start** in the LiveCap dashboard. You should see:

- A WebSocket connection to `wss://dpeohr327wt9l.cloudfront.net/ws/transcribe`
- Status: `101 Switching Protocols`
- Regular `ping`/`pong` frames every 30 seconds

### 4. Live Transcription

Speak a sentence clearly into your microphone. Within 2–5 seconds you should
see a finalized bilingual caption row appear. Use a test sentence such as:

> "Live captions are working correctly for the workshop demonstration."

You should see the English original and the Vietnamese translation side by side.

### 5. Export and Download

1. Click **Stop** to end the session.
2. Click **Export TXT**.
3. Verify the download starts and the file contains the finalized rows.
4. Verify the S3 object exists using the CLI:

```powershell
aws s3 ls s3://livecap-transcripts-dev-720459752315/transcripts/ `
  --profile livecap-codex --region ap-southeast-1
```

### 6. CloudWatch Logs

Check that the backend emitted structured logs during the session:

```powershell
aws logs tail livecap `
  --follow `
  --since 10m `
  --region ap-southeast-1 `
  --profile livecap-codex
```

You should see session lifecycle events: open, audio chunks received, Transcribe
results, Translate calls, session close.

## Verified Production Results

On 2026-07-08, after the blue/green cutover to the target architecture
(custom VPC, private subnets, NAT Gateway, WAF, scale-to-zero, budget alert),
the full production flow passed all of the following:

| Test | Result |
|---|---|
| Health endpoint | `{"status":"healthy","version":"1.0.0"}` ✓ |
| WebSocket open | 101 Switching Protocols ✓ |
| Real 16 kHz PCM transcription (Vietnamese) | Finalized text returned ✓ |
| Real 16 kHz PCM transcription (English) | Finalized text returned ✓ |
| English → Vietnamese translation | Correct translation returned ✓ |
| Ping/pong heartbeat | 30-second interval maintained ✓ |
| Clean session end (Stop button) | Session closed, registry cleared ✓ |
| S3 transcript export | TXT object created in private bucket ✓ |
| Presigned URL download | File downloaded successfully ✓ |
| WAF blocking test | XSS and Log4J probes returned HTTP 403 ✓ |
| ECS scale-to-zero (idle 300 s) | Service scaled to 0 after 5 min idle ✓ |
| ECS self-healing (wake Lambda) | Scaled 0 → 1 and healthy within ≤60 s ✓ |



![End-to-end verification: transcription, translation, and export passing in production](/images/5-Workshop/livecap-transcribe-translate-export-verification.png)

![Runtime security verification: WAF blocking and session limits](/images/5-Workshop/livecap-runtime-security-verification.png)