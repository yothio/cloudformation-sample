VPCとEC2を建てるCloudFormationのテンプレート

```bash
# deploy vpc
$ aws cloudformation create-stack --stack-name VPCStack --template-body file://vpc-template.yaml

# conform outputs
$ aws cloudformation describe-stacks --stack-name VPCStack

# deploy EC2
$ aws cloudformation create-stack \
  --stack-name ApacheServerStack \
  --template-body file://apache-server-template.yaml \
  --parameters ParameterKey=VPCId,ParameterValue=vpc-AAAAAAAAA \          # change vpcId
                ParameterKey=SubnetId,ParameterValue=subnet-BBBBBBB \     # change subnetId
                ParameterKey=AllowedIPAddress,ParameterValue=127.0.0.1/32 # change myIpAddress

```
