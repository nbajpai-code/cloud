# AWS CLI Cheat Sheet

This document serves as a quick reference for common AWS CLI (`aws`) commands, focusing on configuration, compute, storage, and identity management.

## 1. Configuration (`aws configure`)

Manage your AWS credentials and default settings.

| Command | Description |
| :--- | :--- |
| `aws configure` | Interactively set up your Access Key, Secret Key, region, and output format. |
| `aws configure list` | List the current configuration data. |
| `aws configure set [varname] [value]` | Set a specific configuration value. |
| `aws configure get [varname]` | Get a specific configuration value. |

**Example:**
```bash
aws configure
aws configure list
aws configure set region us-west-2
```

## 2. EC2 Instances (`aws ec2`)

Manage Elastic Compute Cloud (EC2) instances.

| Command | Description |
| :--- | :--- |
| `aws ec2 describe-instances` | List detailed information about your instances. |
| `aws ec2 run-instances --image-id [AMI_ID] --count 1 --instance-type t2.micro` | Launch a new instance. |
| `aws ec2 start-instances --instance-ids [ID]` | Start a stopped instance. |
| `aws ec2 stop-instances --instance-ids [ID]` | Stop a running instance. |
| `aws ec2 terminate-instances --instance-ids [ID]` | Terminate (delete) an instance. |

**Example:**
```bash
aws ec2 describe-instances
aws ec2 run-instances --image-id ami-xxxxxxxx --count 1 --instance-type t2.micro --key-name MyKeyPair
aws ec2 stop-instances --instance-ids i-1234567890abcdef0
```

## 3. S3 Storage (`aws s3`)

Manage Simple Storage Service (S3) buckets and objects.

| Command | Description |
| :--- | :--- |
| `aws s3 ls` | List all buckets. |
| `aws s3 ls s3://[bucket-name]` | List content of a specific bucket. |
| `aws s3 mb s3://[bucket-name]` | Make (create) a new bucket. |
| `aws s3 rb s3://[bucket-name]` | Remove (delete) an empty bucket. |
| `aws s3 cp [file] s3://[bucket-name]` | Copy a file to a bucket. |
| `aws s3 rm s3://[bucket-name]/[file]` | Delete a file from a bucket. |

**Example:**
```bash
aws s3 ls
aws s3 mb s3://my-new-bucket
aws s3 cp index.html s3://my-new-bucket/
aws s3 rm s3://my-new-bucket/index.html
```

## 4. IAM (`aws iam`)

Manage Identity and Access Management (IAM) users and roles.

| Command | Description |
| :--- | :--- |
| `aws iam list-users` | List all IAM users. |
| `aws iam create-user --user-name [name]` | Create a new user. |

**Example:**
```bash
aws iam list-users
aws iam create-user --user-name Bob
```

## 5. External Resources

- **Official AWS CLI User Guide**: [Documentation](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)
- **Official AWS CLI Command Reference**: [Command Reference](https://awscli.amazonaws.com/v2/documentation/api/latest/index.html)
- **Awesome AWS**: A curated list of AWS resources - [GitHub](https://github.com/donnemartin/awesome-aws)
- **AWS CLI Cheat Sheet (GitHub)**: [adiii717/aws-cli-cheatsheet](https://github.com/adiii717/aws-cli-cheatsheet)
