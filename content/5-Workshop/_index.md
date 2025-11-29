---
title: "Workshop"
date: "2025-09-09"
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Secure Hybrid Access to S3 using VPC Endpoints

#### Overview

**AWS PrivateLink** provides private connectivity to AWS services from VPCs and your on-premises networks, without exposing your traffic to the Public Internet.

In this lab, you will learn how to create, configure, and test VPC endpoints that enable your workloads to reach AWS services without traversing the Public Internet.

You will create two types of endpoints to access Amazon S3: a Gateway VPC endpoint, and an Interface VPC endpoint. These two types of VPC endpoints offer different benefits depending on if you are accessing Amazon S3 from the cloud or your on-premises location

- **Gateway** - Create a gateway endpoint to send traffic to Amazon S3 or DynamoDB using private IP addresses.You route traffic from your VPC to the gateway endpoint using route tables.
- **Interface** - Create an interface endpoint to send traffic to endpoint services that use a Network Load Balancer to distribute traffic. Traffic destined for the endpoint service is resolved using DNS.

#### Content

1. [Workshop Overview](5.1-Workshop-overview/)
2. [Prerequisites](5.2-Prerequiste/)
3. [Create and Configure Knowledge Base](5.3-Knowledge-Base/)
4. [Test the RAG Chatbot](5.4-Test-Chatbot/)
5. [Client Application Integration (Optional)](5.5-Client-Integration/)
6. [Clean Up Resources](5.6-Cleanup/)
