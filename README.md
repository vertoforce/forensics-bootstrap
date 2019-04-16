# Forensics workspace boostrap

## Abstract

### Problem

Creating and managing a complex full forensics lab is complex and difficult.

### Solution

A docker based forensics lab that can be brought up in one command and will provide lots of forensics tools in an isolated environment


## Usage

### Start

To get started, first run the setup script (this only needs to be done once)
```
bash setup.sh
```

Then bring up the docker stack
```
docker-compose up
```

### Use

To get access to the main terminal / workstation, run this command after the stack is started.

```
docker-compose exec base bash
```

This will drop you in a debian docker image with forensics tools installed (`forensics-all` and `forensics-extra`).
You will have access to all the other docker images in the stack.  The other images are described below.

To access the current directory in the base image, go to `/data`

### Tools


#### Docker-ized sof-elk

#### ZAP

#### Headless chrome

Access at localhost:9222

#### Portainer

To manage docker images

portainer.localhost