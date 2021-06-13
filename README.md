# dynamodb-python
Going through getting started guides for dynamodb and python development. https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GettingStarted.Python.html

# Table of Contents

- [Prerequisites](#prerequisites)
    - [Install Java](#install-java)
    - [Install Python](#install-python)
    - [Install unzip](#install-unzip)
    - [Install dynamodb locally](#install-dynamodb-locally)
- [Getting Started](#getting-started)
    - [Follow tutorial on Amazon docs 😎](#follow-tutorial-on-amazon-docs-😎)

# Prerequisites
## Install Java
Check if you already have java installed by running
```
java -version
```

If you see "command not found" run the below commands to install java
```
sudo apt update
sudo apt install default-jre
```

Verify Java is installed by running
```
java -version
```

You should see the below output if Java installed correctly 
```
openjdk version "11.0.11" 2021-04-20
OpenJDK Runtime Environment (build 11.0.11+9-Ubuntu-0ubuntu2.20.04)
OpenJDK 64-Bit Server VM (build 11.0.11+9-Ubuntu-0ubuntu2.20.04, mixed mode, sharing)
```

## Install Python
```
sudo apt update && upgrade
```
```
sudo apt install python3 python3-pip ipython3
```

## Install unzip
```
sudo apt-get install unzip
```

## Install AWS CLI
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" --output awscliv2.zip
unzip awscliv2.zip
sudo ./aws/install
rm -rf awscliv2.zip
rm -rf aws
```

Now configure aws to use fake credentials for your local dynamodb, enter the following values for each prompt
```
aws configure --profile myprofile
```
```
AWS Access Key ID [None]: "fakeMyKeyId"
AWS Secret Access Key [None]: "fakeSecretAccessKey"
Default region name [None]: x
Default output format [None]:
```

## Install dynamodb locally
Navigate to a directory you want to store a local version of dynamodb
```
mkdir dynamodb-local
cd dynamodb-local
```

Download and extract the java executable for dynamodb
```
curl https://s3.us-west-2.amazonaws.com/dynamodb-local/dynamodb_local_latest.tar.gz --output dynamodb-local-tar.tar.gz
tar -xf dynamodb-local-tar.tar.gz
```

Start dynamodb, use -port to specify another port if the default port (8000) is already taken by another program
```
java -Djava.library.path=./DynamoDBLocal_lib -jar DynamoDBLocal.jar -sharedDb
```

Open a new terminal session and run
```
aws dynamodb list-tables --endpoint-url http://localhost:8000 --profile myprofile
```

You should see the output below if everything setup correctly, try restarting your computer and trying the steps again if you don't see this output

press `q` on your keyboard to exit and get back to the shell after you ran the previous command
```
{
    "TableNames": []
}
(END)
```


# Getting Started

## Follow tutorial on Amazon docs 😎
Head over to [the Amazon docs](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GettingStarted.Python.01.html) to continue through the tutorial, you've set up the dynamodb locally and setting up a connection to web services will be covered at the end of that tutorial

