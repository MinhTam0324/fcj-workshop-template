---
title: "Blog 3"
date: 2024-07-07
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---


# Optimizing LLM Inference on Amazon SageMaker AI with the BentoML LLM Optimizer

Bringing open-source Large Language Models (LLMs) into production is a complex process. The combination of Amazon SageMaker AI and the BentoML LLM Optimizer offers a comprehensive solution to automate the configuration process, thoroughly solving the problem of balancing performance against infrastructure cost.

Below is a detailed breakdown of this approach:

## 1. Challenges in operating LLMs in production

When deploying LLMs, engineers often face major technical barriers:

* **Expensive hardware costs:** Models with billions of parameters require GPUs with large VRAM capacity, consuming a lot of budget if not optimized properly.
* **The trade-off between latency and throughput:** Increasing throughput often leads to increased latency, directly affecting the end-user experience.
* **Time-consuming manual tuning:** Finding the perfect combination of instance type, tensor parallelism, and quantization requires many rounds of trial-and-error.

## 2. How does the BentoML LLM Optimizer solve the problem?

This tool works as an automated probing and benchmarking system, completely replacing guesswork:

* **Automatic profiling:** Simulates real-world traffic patterns to measure the model's performance across many different GPU families (such as G5, P4 on AWS).
* **Standardized packaging:** BentoML automates the containerization of the model and its dependencies, ensuring consistency from the development (dev) environment to the cloud.
* **Deep integration with SageMaker AI:** Leverages AWS's fully-managed infrastructure, enabling smooth auto-scaling and ensuring enterprise-grade network security standards.

## 3. Key points to grasp

* **Efficient VRAM optimization:** The system provides precise parameters to apply quantization (e.g., FP16, INT8), helping large LLMs run stably even on GPUs with limited memory.
* **Recommending the most optimal configuration:** Points directly to the AWS instance type that delivers the highest throughput at the lowest cost per token.
* **Reducing risk:** Prevents over-provisioning that causes waste, or resource shortages that cause bottlenecks when traffic spikes suddenly.

## 4. Value delivered to businesses

Adopting this architecture completely frees the MLOps and Data Engineer teams from writing manual test scripts. It shortens the time-to-market for Generative AI features from weeks down to just a few days, while also making monthly cloud costs transparent and tightly controlled.

## 5. Basic implementation and usage steps

To apply this solution to a real-world project, the general process usually includes the following steps:

Step 1 - Prepare the environment: Install the bentoml library, the AWS support tools (such as bentoML-sagemaker), and set up access permissions (an IAM Role) with the rights to interact with SageMaker and Amazon ECR.

Step 2 - Define the model (Bento Build): Create configuration files (such as service.py and bentofile.yaml) to declare the LLM you want to use. Then, run the BentoML build command to package the model into a standard format.

Step 3 - Launch the LLM Optimizer: Activate BentoML's benchmarking tool. The system automatically spins up test environments on AWS and runs load tests with many different hardware and software parameters.

Step 4 - Evaluate and configure: The Optimizer returns a visual report comparing throughput and latency. Based on this analysis table, you can select the configuration with the most optimal p99 latency and cost for your use case.

Step 5 - Deploy to SageMaker: Use the selected configuration to push the container to Amazon ECR and create a SageMaker Endpoint directly through BentoML's CLI commands, completing the process of bringing the model to production.

The figure below is an overview of the workflow carried out in this article.
![The following figure is an overview of the workflow conducted throughout the post.](/images/blog3_fg1.png)

Link to the post on the AWS Study Group group: [OPTIMIZING LLM DEPLOYMENT PERFORMANCE AND COST ON AMAZON SAGEMAKER AI WITH THE BENTOML LLM OPTIMIZER](https://www.facebook.com/groups/awsstudygroupfcj/posts/2206721756759451/?notif_id=1783392652127913&notif_t=group_post_approved&ref=notif)