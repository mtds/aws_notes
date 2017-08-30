# AWS CLi

## Install AWS Cli

Use VirtualEnv in order to isolate the working environment:
~~~
mkvirtualenv aws_cli
~~~

**Dependencies**: AWS CLI needs Python 2 version 2.6.5+ or Python 3 version 3.3+ and Pip.

~~~
workon aws_cli
pip install awscli
~~~

**Optional**: Enable command completion for the AWS cli: 
* Bash: using the 'aws_bash_completer'
* Zsh: using the 'aws_zsh_completer.sh'

Both of the files are located under the 'bin/' subdirectory of the 'awscli' installation path.

### References

* Official installation guide: https://docs.aws.amazon.com/cli/latest/userguide/installing.html

## Configuration

1. Just launch *aws configure*, it will asks for the following information:
    * AWS Access Key ID
    * AWS Secret Access Key
    * Default region name
    * Default output format (could be: json/table/text)
2. Use environment variables:
    * export AWS_ACCESS_KEY_ID=<access_key>
    * export AWS_SECRET_ACCESS_KEY=<secret_key>

**Security note**: the first choice will create two files under *~/.aws*, called 'config' and 'credentials'. The first one contains just the 
user choice in terms of output format and AWS region but the second one stores the two access key in **clear text** ASCII file.

### References

* Configuring the AWS CLI: https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html
* AWS regions and endpoints: https://docs.aws.amazon.com/general/latest/gr/rande.html

## Commands

### List IAM users

~~~
aws iam list-users
~~~

Output in JSON format:
~~~
{
    "Users": [
        {
            "UserName": "my_username", 
            "PasswordLastUsed": "2017-08-30T19:34:38Z", 
            "CreateDate": "2017-06-19T20:01:02Z", 
            "UserId": "XXXXXXXXXXXXXXXXXXXX", 
            "Path": "/", 
            "Arn": "arn:aws:iam::XXXXXXXXXXXX:user/a_user"
        }
    ]
}
~~~

### List the available AMI images for Amazon Linux

~~~
aws ec2 describe-images --filters "Name=description,Values=Amazon Linux AMI * x86_64 HVM GP2"  --query 'Images[*].[CreationDate, Description, ImageId]' --output text | sort -k 1 | tail
~~~

Output in text format:
~~~
2016-12-20T23:29:45.000Z        Amazon Linux AMI 2016.09.1.20161221 x86_64 HVM GP2      ami-211ada4e
2017-01-20T23:39:57.000Z        Amazon Linux AMI 2016.09.1.20170119 x86_64 HVM GP2      ami-af0fc0c0
[...]
~~~

**Always use the --filters option**: a simple *aws ec2 describe-images* will try to print the entire list of available AMI images.

### Shows the Virtual Private Cloud ID 

~~~
aws ec2 describe-vpcs
~~~

Output in JSON format:
~~~
{
    "Vpcs": [
        {
            "VpcId": "vpc-XXXXXXXXXX",
            "InstanceTenancy": "default",
            "State": "available",
            "DhcpOptionsId": "dopt-XXXXXX",
            "CidrBlock": "172.31.0.0/16",
            "IsDefault": true
        }   
    ]   
}
~~~

### List of available VPC subnets

~~~
aws ec2 describe-subnets --output table
~~~

Reference: https://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Introduction.html

**Firewall rules**: By default the security group allows only SSH connections from the IP of the machine used to reach the EC2 dashboard.
Additional rules can be added with the 'Security Group' option on the 'Network & Security' on the left sidebar or alternatively using the 
link directly in the "Description" of the instance.

### Describe the instance status

~~~
aws ec2 describe-instance-status --instance-ids i-XXXXXXXXXXXXXXXXXX --output=table
~~~

## AWS Cli enhancements/replacements

* https://github.com/donnemartin/saws
* https://github.com/wallix/awless
* https://github.com/achiku/jungle

## References

* Source code repository: https://github.com/aws/aws-cli
* Aliases for AWS cli: https://github.com/awslabs/awscli-aliases

