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
# After running terraform

![terraform to aws instance ec2](https://user-images.githubusercontent.com/85982975/139412185-2957dac3-3b18-4906-8331-14bdda618cfd.png)

# SSH into ec2 instance
default user of ec2 : ec2-user
```sudo ssh -i "Documents/PLAYGROUND/jasondevtools.pem" ec2-user@13.250.30.17 ```
Login template:
```ssh -i "<your-key-pair>.pem" ec2-user@<-aws-instance-public-ip>```

# Login to ec2 instance via SSH
![log in successful to aws instance](https://user-images.githubusercontent.com/85982975/139412140-a738cfcd-aa17-456c-b432-77088c443f4d.png)


# Special Flag for own ip
```
data "http" "myip" {
  url = "http://ipv4.icanhazip.com"
}

```
And whenever you want to place your IP just use data.http.myip.body, example:
```
ingress {
  from_port = 5432
  to_port = 5432
  protocol = "tcp"
  cidr_blocks = ["${chomp(data.http.myip.body)}/32"]
}
```
https://stackoverflow.com/questions/46763287/i-want-to-identify-the-public-ip-of-the-terraform-execution-environment-and-add
