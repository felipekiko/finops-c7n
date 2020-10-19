# FinOps and C7N

Some custodian policies to use in FinOps monitoring

## Notification

All examples have an AWS CloudFormation template, that will create an SNS topic to test your notification, to check if your policy is executed with success, but this message will be delivered in an unreadable format (zlib with base64)

You can uncompress the text, using some zlib and base64 libs, like this example in Python:

```python
zlib.decompress(base64.b64decode(msg))
```

And some online tools do this too, eg.: "http://www.unit-conversion.info/texttools/compress" but be careful...because the message has some sensitive data, like your AWS Account ID

If you want to create an email or other way notification, I recommend look at C7N-Mailer:
https://github.com/cloud-custodian/cloud-custodian/tree/master/tools/c7n_mailer

## Policy

### Unattached Amazon EBS Volumes

This policy check if you have some disks not attached to your account
The CFN file create 2 disks and 1 SNS to send default notification

### Unassociated Elastic IP Addresses

This policy checks if have some Elastic IP unassociated
The CFN file create 2 EIP and 1 SNS to send default notification

### Low Utilization Amazon EC2 Instances

This policy checks if have some ECS with low CPU utilization, and you can configure with your thresholds, changing the instance age days to and CPU percent
The CFN file create 1 EC2 and 1 SNS to send default notification, but to test your policy, you need to adapt it, changing the days to 0

### Idle Load Balancers

This policy checks if have some Load Balancer (Application, Network and Classic) with low utilizantion, and you can configure with your thresholds, changing the instance age days to and requests count
The CFN file create 1 Classic Load Balancer, 1 Application Load Balancer, 1 Network Load Balancer and 1 SNS to send default notification, but to test your policy, you need to adapt it, changing the days to 0

### Amazon RDS Idle DB Instances

This policy checks if have some RDS with low CPU utilization, and you can configure with your thresholds, changing the instance age days to and CPU percent
The CFN file create 1 RDS instance with a SubnetGroup and 1 SNS to send default notification, but to test your policy, you need to adapt it, changing the days to 0

### Underutilized Amazon EBS Volumes

This policy check if you have some disks that are underutilized
The CFN file create 1 instance with 1 disk and 1 SNS to send default notification, to testing, you need to comment on the age of the disk and decrease the value of the threshold

### Underutilized Amazon Redshift Clusters

This policy checks if have some Redshift with low CPU utilization, and you can configure with your thresholds, changing the instance age days to and CPU percent
The CFN file create 1 Redshift instance with a SubnetGroup and 1 SNS to send default notification, but to test your policy, you need to adapt it, changing the days to 0

## To Do

- EBS storage on wrong tier
- Orphaned snapshots
- Instances with wrong families
- Older Snapshots
- Amazon Route 53 Latency Resource Record Sets
- Amazon EC2 Reserved Instance Lease Expiration
- Amazon EC2 Reserved Instances Optimization

## References

Cloud Custodian: https://cloudcustodian.io/

AWS CloudFormation: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide
