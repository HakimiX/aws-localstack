# Local Development with AWS using LocalStack 

* [LocalStack](#localstack)
* [LocalStack with Docker](#localstack-with-docker)

## LocalStack
LocalStack is an open-source mock of the real AWS services. It provides a testing 
environment on your local machine with the same APIs as the real AWS services. 

LocalStack is a Python application designed to run as an HTTP request processor while listening on specific ports. 

## LocalStack with Docker

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
