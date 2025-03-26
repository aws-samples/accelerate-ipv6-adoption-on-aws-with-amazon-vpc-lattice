## Accelerate IPv6 adoption on AWS with Amazon VPC Lattice

This repo includes the Cloudformation template that deploys the architecture shown in Figure-1 below

## PreRequisites
The template will deploy VPCs, EC2 instances and Amazon VPC Lattice constructs into your AWS account. Ensure that you have the right IAM credentials. You can issue `aws configure` to check the AWS permissions.

## Deploying the template

Isse this command to clone the repo:
```
git clone https://github.com/aws-samples/accelerate-ipv6-adoption-on-aws-with-amazon-vpc-lattice/
```

After that, navigate to the right directory:
```
cd accelerate-ipv6-adoption-on-aws-with-amazon-vpc-lattice
```

Use the following command to deploy the CloudFormation template. Please replace the correct SSHClientIP and SSHClientIPv6 addresses. These are the IP and IPv6 addresses of your SSH client machine:

```
aws cloudformation create-stack --stack-name lattice-ipv6-stack \
--template-body file://infra.yaml \
--parameters ParameterKey=SSHClientIP,ParameterValue=a.b.c.d/32 \
ParameterKey=SSHClientIPv6,ParameterValue=2001:db8::1/128 \
--capabilities CAPABILITY_NAMED_IAM
```
Currently the instances do not have HTTPD automatically installed. After creating the stack, please log into the instances and install HTTPD.

## Cleanup
Use this command to delete the stack and all the resources deployed by the stack:
```
aws cloudformation delete-stack --stack-name lattice-ipv6-stack
```

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

