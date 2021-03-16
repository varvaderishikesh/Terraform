### A simple Terraform configuration file to exectue a Count Index

Count Index can be used to modify the configuration of each resource inside the resource block where count is mentioned.

### count_index.tf
```sh
provider "aws" {
  region = "us-west-2"
  access_key = "YOUR-ACCESS-KEY"
  secret_key = "YOUR-SECRET-KEY"
}

variable "elb_names" {
  type = list
  default = ["dev-loadbalancer","stage-loadbalancer","prod-loadbalancer"]
}

resource "aws_iam_user" "lb" {
  name = var.elb_names[count.index]
  count = 3
  path = "/system/"
}
```
