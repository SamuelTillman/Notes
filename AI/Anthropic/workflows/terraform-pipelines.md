# Terraform with Claude Code

Practical examples for using Claude Code with Terraform and IaC pipelines.

## Planning and Applying

```
"run terraform init"
"run terraform plan"
"run terraform plan and save to plan.out"
"apply the saved plan"
"run terraform apply for just the S3 bucket"
```

## State Management

```
"show terraform state"
"list resources in state"
"show state for aws_lambda_function.my_func"
"remove aws_s3_bucket.old_bucket from state"
"import this existing resource into state"
```

## Writing Terraform

```
"add an S3 bucket with versioning enabled"
"create a lambda function with VPC access"
"add an IAM role for the lambda"
"create outputs for the bucket ARN and name"
"add a variable for environment with default dev"
```

## Refactoring

```
"move this resource to a module"
"split this file into separate files by resource type"
"rename this resource from X to Y"
"convert these hardcoded values to variables"
```

## Troubleshooting

```
"why is terraform plan showing this change"
"explain this terraform error"
"what's the difference between these two tfvars files"
"validate my terraform syntax"
```

## Working with Workspaces/Environments

```
"list terraform workspaces"
"switch to the prod workspace"
"show differences between dev.tfvars and prod.tfvars"
"plan with the prod tfvars"
```

## CI/CD Integration

```
"what would the GitHub Actions workflow look like for this"
"add a terraform fmt check to the pipeline"
"create a PR with these terraform changes"
```

## Tips

- Always run `plan` before `apply` and review the output
- Claude can explain complex plans in plain English
- For sensitive changes, ask Claude to walk through step by step
- Use `-target` for surgical changes to specific resources
