Activate access logging on the `Stage` by configuring `AccessLogSettings` to direct logs to the configured.

```yaml
---
AWSTemplateFormatVersion: 2010-09-09
Description: Bad Example of ApiGateway
Resources:
  GoodExampleLogGroup:
    Type: AWS::Logs::LogGroup
    Properties:
      KmsKeyId: "arn:aws:kms:us-west-2:111122223333:key/lambdalogging"
      LogGroupName: "aws/lambda/goodExample"
      RetentionInDays: 30
  GoodApi:
    Type: AWS::ApiGatewayV2::Api
  GoodApiStage:
    Type: AWS::ApiGatewayV2::Stage
    Properties:
      AccessLogSettings:
        DestinationArn: !GetAttr GoodExampleLogGroup.Arn
        Format: json
      ApiId: !Ref GoodApi
      StageName: GoodApiStage
```