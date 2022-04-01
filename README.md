## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 0.13.0 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 3.50 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | >= 3.50 |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [aws_wafv2_web_acl.main](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/wafv2_web_acl) | resource |
| [aws_wafv2_web_acl_association.alb_list](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/wafv2_web_acl_association) | resource |
| [aws_wafv2_web_acl_association.main](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/wafv2_web_acl_association) | resource |
| [aws_wafv2_web_acl_logging_configuration.main](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/wafv2_web_acl_logging_configuration) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_alb_arn"></a> [alb\_arn](#input\_alb\_arn) | Application Load Balancer ARN | `string` | `""` | no |
| <a name="input_alb_arn_list"></a> [alb\_arn\_list](#input\_alb\_arn\_list) | Application Load Balancer ARN list | `list(string)` | `[]` | no |
| <a name="input_allow_default_action"></a> [allow\_default\_action](#input\_allow\_default\_action) | Set to `true` for WAF to allow requests by default. Set to `false` for WAF to block requests by default. | `bool` | `true` | no |
| <a name="input_create_alb_association"></a> [create\_alb\_association](#input\_create\_alb\_association) | Whether to create alb association with WAF web acl | `bool` | `true` | no |
| <a name="input_create_logging_configuration"></a> [create\_logging\_configuration](#input\_create\_logging\_configuration) | Whether to create logging configuration in order start logging from a WAFv2 Web ACL to Amazon Kinesis Data Firehose. | `bool` | `false` | no |
| <a name="input_description"></a> [description](#input\_description) | A friendly description of the WebACL | `string` | `null` | no |
| <a name="input_enabled"></a> [enabled](#input\_enabled) | Whether to create the resources. Set to `false` to prevent the module from creating any resources | `bool` | `true` | no |
| <a name="input_log_destination_configs"></a> [log\_destination\_configs](#input\_log\_destination\_configs) | The Amazon Kinesis Data Firehose Amazon Resource Name (ARNs) that you want to associate with the web ACL. Currently, only 1 ARN is supported. | `list(string)` | `[]` | no |
| <a name="input_logging_filter"></a> [logging\_filter](#input\_logging\_filter) | A configuration block that specifies which web requests are kept in the logs and which are dropped. You can filter on the rule action and on the web request labels that were applied by matching rules during web ACL evaluation. | `any` | `{}` | no |
| <a name="input_name_prefix"></a> [name\_prefix](#input\_name\_prefix) | Name prefix used to create resources. | `string` | n/a | yes |
| <a name="input_redacted_fields"></a> [redacted\_fields](#input\_redacted\_fields) | The parts of the request that you want to keep out of the logs. Up to 100 `redacted_fields` blocks are supported. | `any` | `[]` | no |
| <a name="input_rules"></a> [rules](#input\_rules) | List of WAF rules. | `any` | `[]` | no |
| <a name="input_scope"></a> [scope](#input\_scope) | Specifies whether this is for an AWS CloudFront distribution or for a regional application. Valid values are CLOUDFRONT or REGIONAL. To work with CloudFront, you must also specify the region us-east-1 (N. Virginia) on the AWS provider. | `string` | `"REGIONAL"` | no |
| <a name="input_tags"></a> [tags](#input\_tags) | A map of tags (key-value pairs) passed to resources. | `map(string)` | `{}` | no |
| <a name="input_visibility_config"></a> [visibility\_config](#input\_visibility\_config) | Visibility config for WAFv2 web acl. https://www.terraform.io/docs/providers/aws/r/wafv2_web_acl.html#visibility-configuration | `map(string)` | `{}` | no |
| <a name="input_cloudwatch_log_group_name"></a> [tags](#input\_tags) | The name of the CloudWatch Log Group that will be created to store logs | `string` | `{}` | no |
  | <a name="input_cloudwatch_log_group_name"></a> [tags](#input\_tags) | The name of the CloudWatch Log group that will be created to store the logs. It needs to start with 'aws-waf-logs*' | `string` | `{}` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_web_acl_arn"></a> [web\_acl\_arn](#output\_web\_acl\_arn) | The ARN of the WAFv2 WebACL. |
| <a name="output_web_acl_assoc_acl_arn"></a> [web\_acl\_assoc\_acl\_arn](#output\_web\_acl\_assoc\_acl\_arn) | The ARN of the Web ACL attached to the Web ACL Association |
| <a name="output_web_acl_assoc_alb_list_acl_arn"></a> [web\_acl\_assoc\_alb\_list\_acl\_arn](#output\_web\_acl\_assoc\_alb\_list\_acl\_arn) | The ARN of the Web ACL attached to the Web ACL Association for the alb\_list resource |
| <a name="output_web_acl_assoc_alb_list_id"></a> [web\_acl\_assoc\_alb\_list\_id](#output\_web\_acl\_assoc\_alb\_list\_id) | The ID of the Web ACL Association for the alb\_list resource |
| <a name="output_web_acl_assoc_alb_list_resource_arn"></a> [web\_acl\_assoc\_alb\_list\_resource\_arn](#output\_web\_acl\_assoc\_alb\_list\_resource\_arn) | The ARN of the ALB attached to the Web ACL Association for the alb\_list resource |
| <a name="output_web_acl_assoc_id"></a> [web\_acl\_assoc\_id](#output\_web\_acl\_assoc\_id) | The ID of the Web ACL Association |
| <a name="output_web_acl_assoc_resource_arn"></a> [web\_acl\_assoc\_resource\_arn](#output\_web\_acl\_assoc\_resource\_arn) | The ARN of the ALB attached to the Web ACL Association |
| <a name="output_web_acl_capacity"></a> [web\_acl\_capacity](#output\_web\_acl\_capacity) | The web ACL capacity units (WCUs) currently being used by this web ACL. |
| <a name="output_web_acl_id"></a> [web\_acl\_id](#output\_web\_acl\_id) | The ID of the WAFv2 WebACL. |
| <a name="output_web_acl_name"></a> [web\_acl\_name](#output\_web\_acl\_name) | The name of the WAFv2 WebACL. |
| <a name="output_web_acl_rule_names"></a> [web\_acl\_rule\_names](#output\_web\_acl\_rule\_names) | List of created rule names |
| <a name="output_web_acl_visibility_config_name"></a> [web\_acl\_visibility\_config\_name](#output\_web\_acl\_visibility\_config\_name) | The web ACL visibility config name |
<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
