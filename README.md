# FastAPI for quick prototyping with python and aws lambda

## Create or clone demo app
[Simple Serverless FastAPI with AWS Lambda](https://www.deadbear.io/simple-serverless-fastapi-with-aws-lambda/)

```
git clone https://github.com/xai1983kbu/fastapi-python.git
cd fastapi-python
```

## Create layer
```
cd externalDepsLayer
mkdir -p python/lib/python3.9/site-packages
pip install -r requirements.txt --target python/lib/python3.9/site-packages
cd ..
```

## Deploy
[How to continuously deploy a FastAPI to AWS Lambda with AWS SAM](https://iwpnd.pw/articles/2020-01/deploy-fastapi-to-aws-lambda)
```
sam deploy -g --capabilities  CAPABILITY_IAM
```
Note the output from the SAM deployment process - **ApiUrl**.

## Test

Open in browser
```
{ApiUrl}api/v1/users/users
```
You will see:
```
{"message":"Get Users!"}
```


## Cleanup

1. Delete the stacks
    ```bash
    aws cloudformation delete-stack --stack-name STACK_NAME
    ```
2. Confirm the stacks have been deleted
    ```bash
    aws cloudformation list-stacks --query "StackSummaries[?contains(StackName,'STACK_NAME')].StackStatus"
    ```
