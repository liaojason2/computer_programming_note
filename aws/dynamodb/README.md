# DynamoDB

<!-- TOC -->

- [DynamoDB](#dynamodb)
  - [Frequency use IAM Policy](#frequency-use-iam-policy)

<!-- /TOC -->

## Frequency use IAM Policy

```dynamodb_IAM
  "dynamodb:BatchGetItem",
  "dynamodb:BatchWriteItem",
  "dynamodb:ConditionCheckItem",
  "dynamodb:PutItem",
  "dynamodb:DescribeTable",
  "dynamodb:DeleteItem",
  "dynamodb:GetItem",
  "dynamodb:Scan",
  "dynamodb:Query",
  "dynamodb:UpdateItem"
```

[IAM Policy to Read, Write, Update, and Delete Access on a DynamoDB Table](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/iam-policy-example-data-crud.html)
