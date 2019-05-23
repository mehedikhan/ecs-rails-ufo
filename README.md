# Rails 5 app on ecs using ufo

How to deploy a rails 5 app on AWS ECS using [UFO](https://ufoships.com). 

UFO is a tool that can Build a docker image, Registers the ECS template definition,
Deploys to ECS, Creates an ELB.

## Prerequisite

You will few things to test this template

1. Basic docker knowledge 
2. Aws account or IAM account
3. Setup aws CLI on your local machine
4. Multiple aws profile setup on your local machine
5. How to configure aws profile: https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html


```
~/.aws/credentials

[mehedi-khan]
aws_access_key_id=XXXXXXXXXXX
aws_secret_access_key=XXXXXXXXXXX
```

````
~/.aws/config

[profile mehedi-khan]
region=us-east-1
output=text
````

aws profile can also be configured using aws cli:

````
aws configure --profile mehedi-khan
````

set AWS_PROFILE env variable

````
export AWS_PROFILE=mehedi-khan
````

## Create ECS Stack

Build container 

```
ufo docker build
ufo docker push
```

Deploy to ECS

```
ufo ship ecs-rails-ufo-app 
```

Show process status

```
ufo ps ecs-rails-ufo-app 
```

Scale process

```
ufo scale ecs-rails-ufo-app 2
```


### Cleanup

Delete cloudformation stack

```
ufo destroy ecs-rails-ufo-app
```

