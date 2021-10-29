# Dev Tools Day 04
## Terraform
Assumption that you have already created S3-backend to log in the states


Terraform to add security group of ingress profile

```
  ingress = [
    {
      description      = "Allow SSH"
      from_port        = 22
      to_port          = 22
      protocol         = "tcp"
      cidr_blocks      = ["0.0.0.0/0"]
      ipv6_cidr_blocks = ["::/0"]
      prefix_list_ids  = []
      security_groups  = []
      self             = false
    }
  ]
```


# SSH into ec2 instance
default user of ec2 : ec2-user
```sudo ssh -i "Documents/PLAYGROUND/jasondevtools.pem" ec2-user@13.250.30.17 ```

```ssh -i "<your-key-pair>.pem" ec2-user@<-aws-instance-public-ip>
