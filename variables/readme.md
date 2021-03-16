### A simple Terraform configuration file to exectue variables

Variables are central source from which we can import values to our resources

### variables.tf
```sh
provider "aws" {
  region = "us-east-1"
  access_key = ""
  secret_key = ""
}

resource "aws_security_group" "var_demo" {
  name        = "variables-sg"


  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = [var.vpn_ip]
  }

  ingress {
    from_port   = 443
    to_port     = 443
    protocol    = "tcp"
    cidr_blocks = [var.vpn_ip]
  }

  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = [var.vpn_ip]
  }
}
```

### var.tf
```sh
variable "vpn_ip" {
  default = "116.15.20.30/32"
}
```

### terraform.tfvars
```sh
vpn_ip = "10.0.0.3/32"
```
