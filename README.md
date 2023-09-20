# AWS Lambda Python Jenkins REST API

Use the AWS CloudFormation template to create an AWS Lambda function to Orchestration Jenkins using Python Jenkins REST API.

___
![Python Jenkins API Architecture Diagrams](https://github.com/dakshjat/aws-lambda-python-jenkins/assets/47545538/575acf8b-8292-4fcc-a73b-75d1f9b72d7a)
___
### Prerequisites

1. Install python-jenkins package.

* `pip install -r requirements.txt -t <target_dir>`

2. Create a Jenkins user with the required permissions and generate an API Token to be used as a password.

3. Network connectivity from the AWS Lambda function to the Jenkins server.
___
### Create an AWS CloudFormation stack

**#1.** From the AWS console, create an AWS CloudFormation stack with new resources, specify the template, and enter appropriate parameters.

**#2.** Use the below AWS CLI command to create an AWS CloudFormation stack with a parameter file:

* `aws cloudformation deploy --stack-name aws-lambda-python-jenkins --template-file aws-lambda-python-jenkins.yaml --parameter-overrides file://parameters.json --capabilities CAPABILITY_NAMED_IAM`
___
### Sample Event Payload

**#1. To build a job:**
```json
{
    "job": "<full_project_name>",
    "action": "build",
    "parameters": {
        "<parameter_name1>": "<parameter_value1>",
        "<parameter_name2>": "<parameter_value2>",
        "<parameter_name3>": "<parameter_value3>",
    }
}
```

**#2. To rebuild a job:**
```json
{
    "job": "<full_project_name>",
    "action": "rebuild",
    "build_number": "<build_number>"
}
```

**#3. To validate the job result:**
```json
{
    "job": "<full_project_name>",
    "action": "status",
    "build_number": "<build_number>"
}
```
___

For more information on Python-Jenkins, visit [Python Wrapper for Jenkins REST API](https://python-jenkins.readthedocs.org/en/latest/).