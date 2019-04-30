# Forensics workspace bootstrap

This is my Digital Forensics 2 final project

**Problem**: Creating and managing a full forensics lab is complex and difficult.

**Solution**: A docker based forensics lab that can be brought up in one command and provides forensics tools in an isolated environment.

# Usage

## Features

* Isolated environment for forensics examination that can easily be nuked and rebuilt with minimal effort.
    * Starting environment is clean and deterministic with clear configuration defining the entire environment making documentation of forensics environment simple and easy, especially for formal court cases
* Separation between isolated file storage and local folder accessible by all docker images
    * Easy file access / sharing between otherwise isolated containers
    * Easily separable networks to network-isolate a container
* One line deployment
    * Powerful tools run in docker meaning no setup or dependency collision

## Start

Simply bring up the docker stack to start and leave the terminal window active to view logs.
```
docker-compose up
```

## Files and Isolated files

There are two main stores of files inside the forensics workstation, `isolated files` and `normal files`.

### Normal files

`Normal files` are stored at `/data` in each container and is also accessible via the local `./data` folder.

### Isolated files

`Isolated files` are stored at `/isolated-files` and are stored in a docker container, not accessible via the local filesystem unless you mount the docker volume.  The purpose of this is for sensitive files that you don't want locally accessible in case your anti-virus were to mess with it or to avoid harm to your computer.  Access this via the droppy microservice described below http://droppy.localhost

To remove the isolated files volume and start over, bring down the stack and remove the docker volume
```
docker volume rm isolated-files
```

## Destroying the environment

To destroy the environment and start fresh run the following commands
```
# Ctrl-C in the terminal running the stack
docker-compose down # Make sure stack is down
docker-compose rm # Remove any images
```

If you want to remove local files delete them also
```
rm -r ./data
```

# Tools

## Main workstation

To get access to the main terminal / workstation, run this command after the stack is started.

```
docker-compose exec base bash
```

This will drop you in a debian docker image with forensics tools installed (`forensics-all` and `forensics-extra`).
You will have access to all the other docker images in the stack.  The other images are described below.

To access the current directory in the base image, go to `/data`

## Docker-ized sof-elk

http://kibana.localhost

## ZAP

Zed Attack Proxy is a tool for crawling and testing common security vulnerabilities of a website.  Since it's originally written in java it can be run in a web browser using WebSpring.

http://localhost:8080/?anonym=true&app=ZAP

## Headless chrome

Running chrome in a headless container for browsing to websites that may be malicious or otherwise untested.
Also see [NickJS](https://nickjs.org/) for automation of headless chrome.

http://localhost:9222

## Portainer

Portainer is a tool to manage the docker stack, and add and remove containers

http://portainer.localhost

## Droppy

For file management, especially with isolated files.

http://droppy.localhost

Credentials: `admin / admin`

## Isolated desktop / firefox

See USE_CASES for running a desktop environment and using isolated firefox.
