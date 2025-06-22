# Blue/Green Deployments in AWS Lambda & ECS – Case Study

This project documents how I implemented blue/green deployments for AWS Lambda and ECS (Fargate) in a production environment.

## Problem

We needed a reliable and safe way to roll out new versions of our applications — without disrupting users. Downtime wasn’t an option, and quick rollbacks were critical if something went wrong.

## Solution

I built two automated deployment strategies using AWS-native tools:

### 1. AWS Lambda – Blue/Green via CodeDeploy(default gradual deployment)

- Used Lambda Aliases to shift traffic gradually
- Pre/post-deployment validation using Lambda hooks
- Canary + Linear traffic shifting
- Rollback using CloudWatch alarms

### 2. ECS (Fargate) – Blue/Green via Application Load Balancer

- Deployed new ECS task revisions into a "green" target group
- ALB routed traffic post-validation
- Used appspec.yaml & taskdef.json with CodeDeploy
- Enabled auto rollback on failed health checks

## Tools & Services

- `AWS Lambda`, `ECS (Fargate)`
- `CodeDeploy`, `CloudWatch`
- `ALB`, `IAM`, `CloudFormation`

## Results

Zero downtime  
Safer releases  
Rollback in under 30 seconds  
Improved confidence in shipping to production

## Architecture Diagram

![Blue/Green Deployment Diagram](bluegreen-lambda-ecs.png)

## Notes

> This repository is a generalized case study and **does not** include proprietary code. It reflects architecture and practices I implemented successfully.
