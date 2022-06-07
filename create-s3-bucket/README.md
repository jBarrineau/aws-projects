# Starting off simple

## Using IaC concepts, let's create an S3 bucket with YAML and AWS CloudFormation.

```yaml
Resources:
  S3Bucket:
    Type: "AWS::S3::Bucket"
    DeletionPolicy: Delete
    Properties:
      BucketName: "jb-important-documents-5467"
```

We can deploy this new CloudFormation stack from the CLI:
```cli
aws cloudformation create-stack --stack-name jrb3bucket --template-body file://create_s3.yml
```

This command creates a CloudFormation stack and resources we specified (s3 bucket) into the region our AWS CLI is currently configured to.

We can use `aws cloudformation describe-stacks` at the terminal to verify our new stack has a StackStatus of `CREATE_COMPLETE`.  At this point, our bucket is ready to be utilized.

At this point, we no longer need our S3 bucket.  It's great practice to clean up unused resources to avoid charges, and clutter.

CloudFormation makes it extremely easy to clean up resources created by stacks.  At the command line we can use:
```terminal
aws cloudformation delete-stack --stack-name jrb3bucket
```

Running `aws cloudformation describe-stacks` shows us that we no longer have any active stacks.

