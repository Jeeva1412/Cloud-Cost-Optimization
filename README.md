# 🧹 AWS Cloud Cost Optimization – EBS Snapshot Cleanup Lambda

This project provides an AWS Lambda function designed to **identify and delete stale EBS snapshots** that are no longer associated with any active EC2 instance. It helps in **optimizing storage costs** by removing unused snapshots automatically.

---

## 📌 Problem Statement

EBS snapshots are often retained long after the corresponding volumes or instances are deleted, leading to unnecessary storage charges. This Lambda function solves that by:

- Scanning all EBS snapshots owned by your AWS account.
- Identifying which ones are not tied to active volumes or running/stopped EC2 instances.
- Deleting the snapshots deemed stale.

---

## 🚀 Features

- ✅ Scans all owned EBS snapshots
- ✅ Cross-checks associated volumes and EC2 instance states
- ✅ Deletes snapshots associated with:
  - Non-existent volumes
  - Volumes not attached to any EC2 instance
- ✅ Supports scheduled automatic execution using Amazon EventBridge (CloudWatch Events)
- ✅ Built with Python 3 and Boto3

---

## 🔧 How It Works

1. **Retrieve EBS Snapshots** using `describe_snapshots`.
2. **Get all active EC2 instances** (running and stopped) using `describe_instances`.
3. **Check if each snapshot's volume:**
   - Is missing → delete snapshot
   - Exists but not attached to an active EC2 instance → delete snapshot
4. Logs all actions via **CloudWatch Logs**

---


