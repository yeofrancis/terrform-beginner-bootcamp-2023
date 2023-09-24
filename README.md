# Terraform Beginner Bootcamp 2023

## Install the Terraform CLI

### Considerations with the Terraform CLI changes
The Terraform CLI installation instructions have changed due to gpg keyring deprecation changes.
We needed to refer to the latest Terraform documentation and change the script for install.

[Install Terraform CLI](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)

### Considerations for Linux Distribution
This project is built using Ubuntu.
Pls consider checking your Linux Distrubtion and change accordingly to your distrubtion needs.
[How to check OS Version in Linux](https://www.cyberciti.biz/faq/how-to-check-os-version-in-linux-command-line/)

Example fo checking OS version
```
$ cat /etc/os-release
PRETTY_NAME="Ubuntu 22.04.3 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.3 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
```

#### Refactoring into Bash Scripts

While fixing the Terraform CLI gpg deprecation issues, we noticed that bash scripts steps were a considerable amount more code. So we decided to create a bash script to install the Terraform CLI.

This bash script is located here: [./bin/install_terraform_cli](./bin/install_terraform_cli)
- This will keep the Gitpod Task File ([.gitpod.yml](.gitpod.yml)) tidy.
- This allow us an easier to debug and execute manually Terraform CLi install.
- This allow better portablity for other projects that need to install Terraform CLI

#### Shebang Considerations
A Shebang tells the bash script what program that will interpet the script. eg. '#!/bin/bash'

ChatGPT recommended this format for bash: '#!/usr/bin/env bash'
- for portablity 
- will search for user's PATH for the bash executable

When executing the bash script we can use the './' shorthand notation to execute the script.

https://en.wikipedia.org/wiki/Shebang_(Unix)


#### Linux Permission Consdierations

In order to make our bash scripts executable, we need to change file permission to be executable at user mode.

```sh
chmod u+x ./bin/install_terraform_cli
```
alternatively:

```sh
chmod 744 ./bin/install_terraform_cli
```
https://en.wikipedia.org/wiki/Chmod


### Gitpod Lifecycle (Before, Init, Command)

We need to be careful when using Init because it will not rerun if we restart an existing workspace.
https://www.gitpod.io/docs/configure/workspaces/tasks

