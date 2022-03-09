# IAM

## `PolicyStatement`

### CDK example

```IAM_PolicyStatement
new iam.PolicyStatement({
  actions: [ // List of actions to add to the statement.
    'dynamodb:GetItem',
  ],
  resources: [
    this.exampleTable.tableArn, // Resource ARNs to add to the statement.
  ],
}),
```
