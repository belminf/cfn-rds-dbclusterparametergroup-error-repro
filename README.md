To reproduce, set shell values:

```
STACK_NAME=
SUBNET1=
SUBNET2=
DB_USER=
DB_PASS=
```

Then, create stack:

```
$ aws cloudformation create-stack --stack-name ${STACK_NAME} --capabilities CAPABILITY_NAMED_IAM --parameters ParameterKey=subnet1,ParameterValue=${SUBNET1} ParameterKey=subnet2,ParameterValue=${SUBNET2} ParameterKey=dbusername,ParameterValue=${DB_USER} ParameterKey=dbpassword,ParameterValue=${DB_PASS} --template-body file://template1.yaml
```
