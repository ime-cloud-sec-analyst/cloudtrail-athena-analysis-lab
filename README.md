# cloudtrail-athena-analysis-lab
AWS Lab: Analyze CloudTrail logs with Amazon Athena using SQL queries to monitor AWS events like CreateSecurityGroup. Includes S3 setup, Athena table creation, and result filtering.+
# CloudTrail Athena Analysis Lab

This project demonstrates how to use **Amazon Athena** to analyze **AWS CloudTrail logs** stored in an Amazon S3 bucket. It showcases querying CloudTrail events such as `CreateSecurityGroup` using SQL, offering real-time insights into AWS activity.

---

## 🔍 Lab Overview

### Objective
Use Amazon Athena to query CloudTrail log data from an S3 bucket and extract key security-related events (e.g., security group creations) for auditing and monitoring.

### Tools Used
- **AWS CloudTrail**
- **Amazon S3**
- **Amazon Athena**
- **AWS IAM**
- **SQL**

---

## 🧪 Steps Executed

1. **Enable CloudTrail and store logs in S3**
2. **Create Athena Table from S3 log files**
3. **Configure Query Result Location**
4. **Run SQL queries in Athena:**
   - View events by eventName (`CreateSecurityGroup`)
   - Display username, eventSource, and eventTime

### Sample Query:
```sql
SELECT eventTime, eventSource, eventName, userIdentity.username
FROM "default"."cloudtrail_logs_aws_cloudtrail_logs_256576895597_6c6acb12"
WHERE eventName = 'CreateSecurityGroup'
ORDER BY eventTime DESC
LIMIT 10;
