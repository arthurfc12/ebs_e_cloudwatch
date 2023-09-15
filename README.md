# Elastic Beanstalk com Cloudwatch para notificações
s
<br/>

Antes do deploy crie uma **key pair em ssh** com o comando **ssh -i keygen -t rsa** e use o nome dessa keypair no arquivo tfvars. Além disso você terá que criar um **SNS Topic** pelo dashboard da aws para a notificação dos seus alarmes e um **Route53 Public Hosted Zone** para o domain. Eu utilizei um domain em meu nome para rodar a aplicação


<br/>

Mude as seguintes variáveis no arquivo tfvars antes do deploy.

<br/>

```
region = "us-east-1"

domain_name = "mywebnamearthurfcebs.online"

app_tags = "mywebnamearthurfcebs"

application_name = "mywebnamearthurfcebs_app"

vpc_id = "vpc-00620e11a90df0231"

ec2_subnets = "subnet-03a56e0648b5fe8eb"

elb_subnets = ["subnet-03a56e0648b5fe8eb","subnet-03fd887698d9773fe"]

instance_type = "t3.micro"

disk_size = "20"

keypair = "ssh_ebs"

sshrestrict="12.34.56.78/32"

alarm_sns_topic = "arn:aws:sns:us-east-1:746108472597:NotiTopic"
```

<br/>

Para o deploy use os seguintes comandos

### Deployment

```
terraform init
terraform validate
terraform plan
terraform apply

```

Conceito - B
criação de aplicação terraform com a integração com cloudwatch, porém sem o apoio de diversas regiões simultâneas na aplicação.
