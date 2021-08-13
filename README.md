# awsenv

A simple bash script/command for managing AWS environment credentials.

## Features:

1. Lists all defined AWS named profiles
1. Checks the named profile currently in use
1. Sets AWS credentials environment variables based on selected named profile
1. Sets the following environment variables:
   - `AWS_PROFILE`
   - `AWS_DEFAULT_PROFILE`
   - `AWS_REGION`
   - `AWS_DEFAULT_REGION`
   - `AWS_ACCESS_KEY_ID`
   - `AWS_SECRET_ACCESS_KEY`

## Prerequisite

- Linux or Mac OS
- Install AWS Cli

## Installation

You can download the `awsenv` script to the a `/bin` directory of your choice. For example: `/usr/local/bin`

```
AWSENV_PATH=/usr/local/bin/awsenv
curl -o $AWSENV_PATH https://raw.githubusercontent.com/linsight/awsenv/main/awsenv
chmod +x $AWSENV_PATH
echo 'awsenv() { eval "$('$AWSENV_PATH' $@)" }' >> ~/.zshrc
```

## Usage

`awsenv`: Shows the current profile/environment

`awsenv ls`: Lists all the defined profile names

`awsenv use <profile_name>`: sets all AWS credentials environment variables for given named profile;

## What's next

1. `awsenv` manages AWS credentials environment variables in your current shell session. This means that if you start a new terminal, the new terminal is likely to have no AWS credentials environment or a different AWS credentials environment from the one you are working on. To avoid confusion. It is recommended to `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` environment variables from your start-up script (e.g. `~/.zshrc`). You can keep the `AWS_PROFILE` and `AWS_REGION`. When you run `awsenv`, it will create the `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` environment variables for your current shell session based on the `AWS_PROFILE`. If `AWS_PROFILE` is not available, you will be asked to run `awsenv use <profile>`.

2. Once `awsenv` sets the AWS credentials environment for you. You don't need to append `--profile` option to the AWS CLI commands anymore. The AWS CLI will use the profile set with the `AWS_PROFILE` variable.

3. Feel free to enhance the script for other variables like `AWS_SESSION_TOKEN`
