# AWS Lambda

*Definition*: AWS Lambda is a compute service that lets you run code without provisioning or managing servers. AWS Lambda executes your code only when needed and scales automatically, from a few requests per day to thousands per second. You pay only for the compute time you consume - there is no charge when your code is not running. [...]
You can use AWS Lambda to run your code in response to events, such as changes to data in an Amazon S3 bucket or an Amazon DynamoDB table; to run your code in response to HTTP requests using Amazon API Gateway; or invoke your code using API calls made using AWS SDKs.

Reference: https://docs.aws.amazon.com/lambda/latest/dg/welcome.html

## 'Hello World' as Lambda Function

Reference: https://docs.aws.amazon.com/lambda/latest/dg/getting-started-create-function.html

## Useful functions from AWS Cli

List the details about all the Lambda functions deployed:
```
aws lambda list-functions
```

Get the configuration details of a specific Lambda function:
```
aws lambda get-function-configuration --function-name my_lambda_function
```

Invoke a Lambda function from the cmd line:
```
aws lambda invoke --function-name my_lambda_function "Parameter 1","Parameter 2",[...]
```

*NOTE*: By default the output result will always be formatted in JSON.

Reference: https://docs.aws.amazon.com/cli/latest/reference/lambda/index.html#cli-aws-lambda

## Build and test Serverless locally

AWS SAM Local is a CLI tool for local development and testing of Serverless applications.

Features:
* Develop and test your Lambda functions locally with `sam local` and `Docker`
* Invoke functions from known event sources such as Amazon S3, Amazon DynamoDB, Amazon Kinesis, etc.
* Start local API Gateway from a SAM template, and quickly iterate over your functions with hot-reloading
* Validate SAM templates

References:
* https://github.com/awslabs/aws-sam-local
* https://docs.aws.amazon.com/lambda/latest/dg/test-sam-local.html
* https://aws.amazon.com/blogs/aws/new-aws-sam-local-beta-build-and-test-serverless-applications-locally/

## Additional References

* AWS Lambda FAQ (https://aws.amazon.com/lambda/faqs/)
* How to Create Your First Python 3.6 AWS Lambda Function (https://www.fullstackpython.com/blog/aws-lambda-python-3-6.html)
* AWS Lambda, Zappa, Flask and Python 3 (https://andrich.blog/2017/02/12/first-steps-with-aws-lambda-zappa-flask-and-python/)

## Useful Tools

* Zappa makes it easy to build and deploy server-less, event-driven Python applications (including, but not limited to, WSGI web apps) on AWS Lambda + API Gateway. (https://github.com/Miserlou/Zappa)
* Various popular libraries, pre-compiled to be compatible with AWS Lambda. (https://github.com/Miserlou/lambda-packages)
