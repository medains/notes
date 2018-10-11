# Notes on AWS

1. [CloudFormation](#CloudFormation)
1. [AWS CLI](#AWS CLI)

## CloudFormation

* Templates
  * If the previous build failed, may require deleting the stack to redeploy

## AWS CLI

### What is my ARN

```bash
aws sts get-caller-identity
```

### Change role

Performing actions in the AWS CLI under a different IAM role can be awkward.  So here's how to assume a role for a session

```bash
unset AWS_SESSION_TOKEN AWS_SECRET_ACCESS_KEY AWS_ACCESS_KEY_ID
AWS_DEFAULT_OUTPUT=json aws sts assume-role \
  --role-arn "TARGET" --role-session-name AWSCLI-Session \
  --serial-number "YOURMFA ARN" \
  --token-code "CURRENT CODE" > assume-response.json
eval `gron -m assume-response.json | fgrep json.Credentials. | fgrep -v Expiration | sed 's/json.Credentials./export AWS_/;s/AccessKeyId/ACCESS_KEY_ID/;s/SecretAccessKey/SECRET_ACCESS_KEY/;s/SessionToken/SESSION_TOKEN/; s/ = /=/'`
```

When finished, unset the AWS environment variables again

### Set parameters

```bash
aws ssm put-parameter --profile PROFILE --name '/PATH/KEY' --value 'VALUE' --type SecureString
```

### Read parameters

```bash
aws ssm get-parameters-by-path --profile PROFILE --path '/some-path/'
```

### Query Dynamodb objects

```bash
aws dynamodb scan --profile PROFILE  --table-name TABLE --filter-expression "field.field = :id" --expression-attribute-values '{":id":{"S":"VALUE"}}'
```

