# AWS CLI with Claude Code

Practical examples for using Claude Code to interact with AWS.

## Profile Management

```
"list my aws profiles"
"which aws account am I using"
"login to the prod profile"
"switch to the dev profile"
```

## Lambda Operations

```
"list lambdas in us-east-1"
"get the code for lambda function X"
"update lambda X with this zip file"
"check the status of lambda X"
"show me the environment variables for lambda X"
"download a backup of lambda X"
```

## S3 Operations

```
"list buckets"
"list files in s3://bucket-name/prefix/"
"download s3://bucket/file.txt to local"
"upload local-file.txt to s3://bucket/"
"delete s3://bucket/file.txt"
"sync this folder to s3://bucket/prefix/"
```

## IAM Operations

```
"list access keys for user X"
"delete access key AKIA... for user X"
"what policies are attached to role X"
"list users in this account"
```

## EC2 Operations

```
"list running instances"
"describe instance i-xxx"
"stop instance i-xxx"
"show security groups for instance i-xxx"
```

## CloudWatch

```
"show recent logs for lambda X"
"tail logs for /aws/lambda/function-name"
"search logs for ERROR in the last hour"
```

## Tips

- Always specify `--profile` or let Claude know which profile to use
- Claude will ask for confirmation before destructive operations
- For cross-account work, tell Claude which account/profile for each resource
- SSO tokens expire - if you get auth errors, ask Claude to re-login
