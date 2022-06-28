# Local Development with AWS using LocalStack 

* [LocalStack](#localstack)
    * [Docker Compose](#docker-compose)
    * [Configure Local AWS CLI profile](#configure-local-aws-cli-profile)
    * [Connecting to LocalStack](#connecting-to-localstack)

## LocalStack
LocalStack is an open-source mock of the real AWS services. It provides a testing 
environment on your local machine with the same APIs as the real AWS services. 

LocalStack is a Python application designed to run as an HTTP request processor while listening on specific ports. 

### Docker Compose
The base `docker-compose.yml` file from the [LocalStack](https://github.com/localstack/localstack/blob/master/docker-compose.yml) repository is used. 

The default behavior of LocalStack is to spin up all the supported AWS services
with each of them listening on port 4566. You can override this behavior by 
setting a few environment variables. 

You can configure LocalStack to spin up a limited set of services by using a 
comma-separated list of AWS service names as value for the environment variable 
`services`:
```yaml
environment:
    - SERVICES: s3, lambda, dynamodb
```
In the example above, the environment variable `SERVICES` is set to the name 
of the AWS services we want to use in the application (s3, lambda, and dynamodb).

### Configure Local AWS CLI profile
Configure a fake AWS CLI profile to be able to invoke the services provided by LocalStack. 
```shell
# Create a profile called localstack (profile name can be anything)
aws configure --profile localstack
```
This will prompt for the AWS Access Key, Secret Key, and an AWS region. Provide any 
dummy value for the credentials and a valid region name like `eu-west-1`, but the none
of the values can be left blank. 

Unlike AWS, LocalStack doens't validate these credentials but complains if not profile is set. The profile is stored in `~/.aws/config` 


### Connecting to LocalStack
Todo...
