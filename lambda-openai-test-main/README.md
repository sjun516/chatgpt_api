# Build
```
docker build -t coredot/lambda310 .
docker run --rm -v "${PWD}":/var/task coredot/lambda310
```

# Init
## File Upload
```
aws s3 cp deploy_package.zip s3://your-lambda-deployment --profile default
```

## AWS Lambda Function Create
```
aws lambda create-function --function-name this-func-name --runtime python3.9 --code S3Bucket=your-lambda-deployment,S3Key=deploy_package.zip --handler lambda_function.lambda_handler --role arn:aws:iam::4010101010:role/lambda-role --region ap-northeast-2 --profile default --timeout 30 --memory-size 128
```


# Update
## AWS Lambda Function Update
```
aws lambda update-function-code --function-name this-func-name --zip-file fileb://deploy_package.zip --profile default
```
