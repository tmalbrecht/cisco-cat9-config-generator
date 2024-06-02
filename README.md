[![python](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org)
![Repo Size](https://img.shields.io/github/repo-size/Sulstice/global-chem)
[![Code Style](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/ambv/black)

# Config generator for Cisco Catalyst 9000 switches

The script is designed to extract switch variables from an Excell spreadsheet to generate switch configurations in bulk.

## Getting Started

### Prerequisites

Before installing the software, ensure you have the following prerequisites:

 * The script is tested in a windows environment but I expect it also to work in linux.
 * Python Version: The code is developed in Python 3.12.1. Although it has not been tested on other versions, newer versions should generally be compatible.
 * Library Dependencies: Refer to the requirements.txt file for all necessary libraries. It is recommended to use a separate virtual environment (venv) for installation to avoid conflicts with existing packages.

### Installation

Go to the directory where you intend to save the repository and execute the following command:

```
git clone https://github.com/tmalbrecht/cisco-cat9-config-generator.git
```

Move into the directory and setup a Python virtual environment:

```
cd cisco-cat9-config-generator
python3 -m venv venv 
source venv/bin/activate
```

Install all required libraries:

```
pip3 install -r requirements.txt
```


## Preperation

Fill in an Excell spreadsheet file for every switch you want to generate code for. Put these files in the folder 'switch_variables' inside the srcipts directory.

See the following folder for example xlsx files you can use:
https://github.com/tmalbrecht/cisco-cat9-config-generator/tree/main/switch_variables

Create the .env file and edit it:
```
touch .env
nano .env
```

Enter your credentials and email details into the file as shown below; you can copy and paste them directly into nano:
```
# Secrets needed to generate config
# Leave blank if you don't want to store them here for security reasons.
# The script will prompt you when excuting it
ADMIN_PASS = "admin_pass"
SNMP_USER_PASS = "snmp_pass"
RADIUS_KEY = "radius_key"
```
Close the file by typing ctrl + x, type 'y' and after press enter.

## Security 

Please ensure that your secrets are not stored in a script within a directory where others have read permissions. If the secrets are not specified in the .env file, you will be prompted to enter them when executing the script. The getpass() function is used to securely handle your passwords, ensuring it remains hidden at all times.

## Usage
Navigate into the project directory and execute main.py:

```
python main.py
```

If you haven't entered any secrets in the .env file, you will be prompted to provide them. The getpass() function is used to ensure that your passwords remain hidden.

After the script will generate config for every switch that a Excell spreadsheet was provided for. You can find the generated configs in the folder 'generated_configs'.
