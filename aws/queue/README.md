# Queue

<!-- TOC -->

- [Queue](#queue)
  - [BLS & CDK compare](#bls--cdk-compare)
    - [`RedrivePolicy`](#redrivepolicy)
    - [Bind Lambda](#bind-lambda)

<!-- /TOC -->

## BLS & CDK compare

### `RedrivePolicy`

[SQS Redrive Policy](https://awslabs.github.io/serverless-rules/rules/sqs/redrive_policy/)
BLS `RedrivePolicy` corresponding to CDK `deadLetterQueue`

```yaml
  ConvertExampleDeadLetterQueue:
    Type: AWS::SQS::Queue
    Properties:
      QueueName: ConvertExampleDeadLetter
      VisibilityTimeout: 300

  ConvertExampleQueue:
    Type: AWS::SQS::Queue
    Properties:
      QueueName: ConvertExample
      VisibilityTimeout: 5
      RedrivePolicy:
        deadLetterTargetArn: !GetAtt ConvertExampleDeadLetterQueue.Arn
        maxReceiveCount: 2
```

```typescript
import * as sqs from '@aws-cdk/aws-sqs';

const convertExampleDeadLetterQueue = new sqs.Queue(this, 'ConvertExampleDeadLetterQueue', {
  queueName: 'ConvertExampleDeadLetter',
  visibilityTimeout: core.Duration.seconds(300),
});
const convertExampleQueue = new sqs.Queue(this, 'ConvertExampleQueue', {
  queueName: 'ConvertExampleQueue',
  visibilityTimeout: core.Duration.seconds(5),
  deadLetterQueue: {
    maxReceiveCount: 2,
    queue: convertExampleDeadLetterQueue,
  },
});
```

### Bind Lambda

```Lambda bind sqs example
declare const exampleFunction: NodejsFunction;
exampleFunction.addEventSource(new lambdaEventSources.SqsEventSource(convertDiagnosticReportQueue, {
  batchSize: 1,
}));
```
