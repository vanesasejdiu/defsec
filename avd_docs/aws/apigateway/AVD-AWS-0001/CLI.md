Access logging can be configured on an existing stage using the `update-stage` command; specify the `rest-api-id` and the `stage-name` and configure `/*/*/logging/dataTrace` to `true`

```bash
aws apigateway update-stage --rest-api-id 1234123412 --stage-name 'dev' --patch-operations op=replace,path=/*/*/logging/dataTrace,value=true
```