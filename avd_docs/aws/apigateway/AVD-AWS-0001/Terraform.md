---
additional_links:
  - https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/apigatewayv2_stage#access_log_settings
---

Activate access logging on API Gateway stage by configuring the `access_log_settings` block in the `aws_api_gateway_stage`.

```hcl
resource "aws_cloudwatch_log_group" "good_example" {
  name = "good_example"

  tags = {
    Environment = "production"
    Application = "serviceA"
  }
}

resource "aws_api_gateway_stage" "good_example" {
   deployment_id = aws_api_gateway_deployment.example.id
   rest_api_id   = aws_api_gateway_rest_api.example.id
   stage_name    = "example"
 
   access_log_settings {
     destination_arn = aws_cloudwatch_log_group.good_example.arn
     format          = "json"
   }

     tags = {
    Environment = "production"
    Application = "serviceA"
  }
}
```