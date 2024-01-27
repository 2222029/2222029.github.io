# getwind (https://github.com/2222029/wind)

Create wind and weather graphics for selected locations.

Script file is getwind.py (https://github.com/2222029/wind/blob/main/getWind.py), private repository!
Ouptput to ./2222029.github.io.

Uses the Meteomatis API (https://www.meteomatics.com/en/sign-up-weather-api-free-basic-account/) for retrospective data and predictions if live data unavailable.

Run locally or automated using github actions (https://docs.github.com/en/actions) with self hosted runner.

Tested with self hosted runner on Raspberry Py Desktop, virtualized X64 archtecture in virtualbox.
See configration below.

Example see https://2222029.github.io

Physical Raspberry: todo

# Common configuration

## Check python version

python 3.9.2

## Install requirements

- pip install pandas==2.20
- pip install matplotlib==3.8.2
- pip install meteomatics
- pip install lxml

# Test locally 
## Get software from github

git clone https://oauth2:TOKEN@github.com/2222029/wind

## Get output from github

git clone --depth 1 https://oauth2:TOKEN@github.com/2222029/2222029.github.io

## Run script

python ./wind/getWind.py

## Check output
index.html and svg files in ./2222029.github.io

# Automation with github actions
## Install and configure github runner on Raspberry Py Desktop

### Install dotnet (debian 11)

https://learn.microsoft.com/en-us/dotnet/core/install/linux-debian

## Install github runner

### Create a folder
mkdir actions-runner && cd actions-runner

### Download the latest runner package
curl -O -L https://github.com/actions/runner/releases/download/v2.311.0/actions-runner-linux-x64-2.312.0.tar.gz
### Extract the installer
tar xzf ./actions-runner-linux-x64-2.312.0.tar.gz

### Install dependecies

sudo ./bin/installdependencies.sh

### Disable ipv6 (timeout bug)
https://www.itzgeek.com/how-tos/linux/debian/how-to-disable-ipv6-on-debian-9-ubuntu-16-04.html

### Configure runner
See https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners
See https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners/adding-self-hosted-runners

Adding a runner in Github Actions will give a command like

./config.sh --url https://github.com/2222029/wind --token TOKEN
with unique token.

Create the runner with name raspx64. Tags X64, rasp-x64

### Run runner
 ./run.sh

## Workflow file 
The workflow file for the self hosted runner is getWind-rasp-x64.yml (https://github.com/2222029/wind/blob/main/.github/workflows/getWind-rasp-x64.yml).
It is configured for a manual run and will update the repositorry https://github.com/2222029/2222029.github.io.




