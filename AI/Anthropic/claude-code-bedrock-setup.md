# Claude Code Setup with AWS Bedrock

## 1. Install Claude Code

```bash
# Option A: npm
npm install -g @anthropic-ai/claude-code

# Option B: Homebrew (macOS)
brew install claude-code
```

Verify installation:
```bash
claude --version
```

## 2. Enable Claude Models in Bedrock

Before configuring Claude Code, make sure Claude models are enabled in your AWS account:

1. Go to AWS Console > Bedrock > Model access
2. Request access to Anthropic Claude models (Claude Sonnet, Claude Haiku, etc.)
3. Wait for access to be granted (usually instant, sometimes a few minutes)

## 3. Configure AWS Credentials

Claude Code uses your AWS credentials to call Bedrock. Set up one of these:

### Option A: SSO (recommended for NBA)
```bash
aws configure sso
# Follow prompts to set up your SSO profile

# Then login before using Claude:
aws sso login --profile your-profile-name
```

### Option B: Environment Variables
```bash
export AWS_ACCESS_KEY_ID=your-access-key
export AWS_SECRET_ACCESS_KEY=your-secret-key
export AWS_REGION=us-east-1
```

### Option C: IAM credentials file
```bash
aws configure
# Enter your access key, secret key, and region
```

## 4. IAM Permissions Required

Your IAM user/role needs these permissions:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "bedrock:InvokeModel",
        "bedrock:InvokeModelWithResponseStream"
      ],
      "Resource": "arn:aws:bedrock:*::foundation-model/anthropic.*"
    }
  ]
}
```

## 5. Configure Claude Code for Bedrock

```bash
# Set Bedrock as the provider
claude config set provider bedrock

# Set your AWS region (must have Claude models enabled)
claude config set bedrock.region us-east-1

# Optional: specify a profile if using named AWS profiles
claude config set bedrock.profile your-profile-name
```

## 6. First Run

```bash
# Navigate to your project
cd your-project

# Start Claude Code
claude

# Or ask a one-off question
claude "explain this codebase"
```

## Troubleshooting

### "Access denied" or "Model not available"
- Check that Claude models are enabled in Bedrock console
- Verify your IAM permissions include `bedrock:InvokeModel*`
- Make sure you're using a region where Bedrock Claude is available (us-east-1, us-west-2, etc.)

### SSO token expired
```bash
aws sso login --profile your-profile-name
```

### Wrong AWS account
```bash
# Check which account you're using
aws sts get-caller-identity

# Switch profiles if needed
export AWS_PROFILE=correct-profile-name
```

## Useful Commands

```bash
# Check current config
claude config list

# Change model (default is Claude Sonnet)
claude config set model claude-sonnet-4-20250514

# Reset config
claude config reset
```

## Questions?

Reach out to the team if you hit any issues!
