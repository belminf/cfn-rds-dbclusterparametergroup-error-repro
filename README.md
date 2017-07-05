Per [doc](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-rds-dbparametergroup.html), `Tags` are described as `Update requires: No interruption`. However, updating via CloudFormation leads to the following error:

    RDS DBCluster tags cannot be updated.

To reproduce via CLI, set environment values for CloudFormation parameters:

```
STACK_NAME=
SUBNET1=
SUBNET2=
DB_USER=
DB_PASS=
```

Then, create stack (takes ~30 minutes):

```
$ aws cloudformation create-stack --stack-name ${STACK_NAME} --capabilities CAPABILITY_NAMED_IAM --parameters ParameterKey=subnet1,ParameterValue=${SUBNET1} ParameterKey=subnet2,ParameterValue=${SUBNET2} ParameterKey=dbusername,ParameterValue=${DB_USER} ParameterKey=dbpassword,ParameterValue=${DB_PASS} --template-body file://template1.yaml
```

Finally, update:

```
$ aws cloudformation update-stack --stack-name ${STACK_NAME} --capabilities CAPABILITY_NAMED_IAM --parameters ParameterKey=subnet1,ParameterValue=${SUBNET1} ParameterKey=subnet2,ParameterValue=${SUBNET2} ParameterKey=dbusername,ParameterValue=${DB_USER} ParameterKey=dbpassword,ParameterValue=${DB_PASS} --template-body file://template2.yaml

```
