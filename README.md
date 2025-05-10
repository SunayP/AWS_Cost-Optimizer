# AWS Cloud Cost Optimization – Identifying Stale EBS Snapshots

##  Overview

Cost optimization in cloud environments is crucial, especially for startups and mid-scale organizations. This project uses an AWS Lambda function written in Python to automatically identify and delete stale EBS snapshots that are no longer associated with active EC2 volumes, helping reduce unnecessary storage costs.

---

## Project Highlights

- Automates the identification of unused EBS snapshots
- Utilizes AWS Lambda, EC2, EBS, IAM, and CloudWatch
- Reduces cloud spend by cleaning up stale backups
- Supports scheduled cleanup with CloudWatch Events

---

## Architecture

- **AWS Lambda** function written in Python (Boto3)
- **CloudWatch Scheduler** (EventBridge) to run daily/weekly
- **IAM Roles & Policies** for secure access to EC2 and EBS APIs

---

## How It Works

1. Fetch all EBS snapshots owned by your AWS account.
2. Retrieve a list of active EC2 volumes and EC2 instances.
3. Check if each snapshot is still associated with a volume or instance.
4. If not used recently (based on timestamp or metadata), **delete it**.
5. Schedule this function using **CloudWatch Events**.

---

## Permissions Required

The Lambda execution role should have the following **minimum permissions**:

- `ec2:DescribeSnapshots`
- `ec2:DescribeVolumes`
- `ec2:DescribeInstances`
- `ec2:DeleteSnapshot`

>  Follow the **principle of least privilege** by creating a custom IAM policy attached to your Lambda execution role.

---

## Automation

- Use CloudWatch to run the Lambda function at intervals (daily/weekly).
- Monitor executions and logs using **CloudWatch Logs**.

---

## Related Concepts

- What are stale resources in cloud computing?
- How can Lambda functions help in cost optimization?
- What is the role of DevOps in cloud resource management?

---

## Learnings & Takeaways

- Importance of cloud cost optimization
- Real-world automation using AWS Lambda and Boto3
- IAM best practices for secure automation
- Integration of AWS services for end-to-end cleanup

---

## Tech Stack

- AWS Lambda
- AWS EC2 / EBS
- AWS IAM
- AWS CloudWatch (Events & Logs)
- Python (Boto3)

---

## Future Scope

- Extend this project to detect:
  - Unused Elastic IPs
  - Stale AMIs
  - Idle Load Balancers or S3 buckets
- Archive old snapshots to S3 Glacier instead of deleting

---

## 🙋 About Me

I'm currently learning AWS and exploring real-world use cases through automation projects like this. Feedback and contributions are welcome!
