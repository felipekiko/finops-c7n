# FinOps and C7N

Some custodian policies to use in FinOps monitoring

## Notification

All examples has a AWS CloudFormation template, that will create a SNS topic to test your notification, to check if your police are executed with success, but this message will be delivery in a unreable format (zlib with base64)

You can uncompress the text, using some zlib and base64 libs, like this example in Python:

```python
zlib.decompress(base64.b64decode(msg))
```

And some online tools do this to, eg.: "http://www.unit-conversion.info/texttools/compress" but be carreful...because the message has some sensetive data, like your AWS Account ID

If you want create a email or other way notification, I recomend look at C7N-Mailer:
https://github.com/cloud-custodian/cloud-custodian/tree/master/tools/c7n_mailer

## EBS

### Unattached Amazon EBS Volumes

This police check if you have some disks not attached in your account
The CFN file create 2 disks and 1 SNS to send default notification

## To Do

- Low Utilization Amazon EC2 Instances
- Idle Load Balancers
- Underutilized Amazon EBS Volumes
- Unassociated Elastic IP Addresses
- Amazon Route 53 Latency Resource Record Sets
- Amazon RDS Idle DB Instances
- Underutilized Amazon Redshift Clusters
- Amazon EC2 Reserved Instance Lease Expiration
- Amazon EC2 Reserved Instances Optimization

## References

Cloud Custodian: https://cloudcustodian.io/

AWS CloudFormation: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide
