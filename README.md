# terraform-aws-api-gateway-function

Makes mapping Lambda functions to API gateways less messy and error prone.

## Features

* Creates the permission for API gateway to execute the specified Lambda function.
* Creates and keeps track of the 3 different resources required to map the function to the API gateway.

```js
module "apigw-lambda-function" {
  source = "github.com/alanjjenkins/terraform-aws-api-gateway-function"

  account_number          = "${var.account_number}"
  permission_statement_id = "apigw-lambda-function-permission-${var.envtype}"
  lambda_function_arn     = "${aws_lambda_function.lambda.arn}"
  rest_api_id             = "${aws_api_gateway_rest_api.api.id}"
  resource_id             = "${aws_api_gateway_resource.resource.id}"
  resource_path           = "${aws_api_gateway_resource.resource.id}"
  http_method             = "POST"
}
```
## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| account_number | Your AWS account number | string | `` | yes |
| permission_statement_id | VPC configuration for the Lambda function | string | `` | yes |
| lambda_function_arn | VPC configuration for the Lambda function | string | `` | yes |
| rest_api_id | VPC configuration for the Lambda function | string | `` | yes |
| resource_id | VPC configuration for the Lambda function | string | `` | yes |
| resource_path | VPC configuration for the Lambda function | string | `` | yes |
| http_method | VPC configuration for the Lambda function | string | `` | yes |
| region | The region you want to create the api gateway method in. | string | `eu-west-1` | no |
| authorization | The type of authorization used for the method (NONE, CUSTOM, AWS_IAM). | string | `NONE` | no |
