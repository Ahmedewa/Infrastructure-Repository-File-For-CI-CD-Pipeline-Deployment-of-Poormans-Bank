# Infrastructure-Repository-File-For-CI-CD-Pipeline-Deployment-of-Poormans-Bank
Infrastructure Repository File (IaC Configuration)
Configuration files for Terraform, Kubernetes, and Cloud Formation.


Terraform
hcl
provider "aws" {
  region = "af-1-=los-1a"
}

resource "aws_instance" "poormansbank" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  tags = {
    Name = "PoormansBank"
  }
}
Kubernetes
yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: poormansbank
spec:
  replicas: 2
  selector:
    matchLabels:
      app: poormansbank
  template:
    metadata:
      labels:
        app: poormansbank
    spec:
      containers:
      - name: poormansbank
        image: poormansbank:latest
        ports:
        - containerPort: 8080


CloudFormation
yaml
Resources:
  PoormansBankInstance:
    Type: "AWS::EC2::Instance"
    Properties:
      InstanceType: "t2.micro"
      ImageId: "ami-0c55b159cbfafe1f0"
      Tags:
        - Key: "Name"
          Value: "PoormansBank"



