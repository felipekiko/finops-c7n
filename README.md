# FinOps and C7N

Some custodian policies to use in FinOps monitoring

# EBS

## Unattached Amazon EBS Volumes

This police check if you have some disks not attached in your account

The CFN file create 2 disks and 1 SNS to send default notification, only to test and see if police works
To uncompress the text that you will received, you need uncompress zlib in base64

In Python you can do this:
```python
zlib.decompress(base64.b64decode(msg))
```

And some online tools do this, like this "http://www.unit-conversion.info/texttools/compress" but be carreful, because the message has some sensetive data, like your AWS Account ID

But, if you want create a email or other way notification, I recomend look at C7N-Mailer:
https://github.com/cloud-custodian/cloud-custodian/tree/master/tools/c7n_mailer
