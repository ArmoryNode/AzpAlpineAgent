<h1>AzpAlpineAgent</h1>

![License](https://img.shields.io/badge/license-Apache_2.0-orange.svg)
![Build Status](https://github.com/armorynode/azpalpineagent/actions/workflows/build-and-push-image.yml/badge.svg)

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
- [Running Prebuilt Image](#running-prebuilt-image)
- [Building Manually](#building-manually)
- [Using Docker Compose](#using-docker-compose)

## Introduction

A simple Azure Pipelines build agent using an Alpine base image, mainly for building ASP.NET applications.

## Running Prebuilt Image

1. Pull the image from the GitHub container registry:
   ```sh
   docker pull ghcr.io/armorynode/azpalpineagent:main
   ```
2. Run the Docker container:
    ```sh
	# Linux/MacOS
    docker run -d ghcr.io/armorynode/azpalpineagent:main \
		-e AZP_URL="Your DevOps Organization URL" \
		-e AZP_TOKEN="Your Azure DevOps PAT" \
		-e AZP_AGENT_NAME="Your Agent Name" \
		-e AZP_POOL="Your Agent Pool Name"
    ```

	```PowerShell
	# Windows
	docker run -d ghcr.io/armorynode/azpalpineagent:main `
		-e AZP_URL="Your DevOps Organization URL" `
		-e AZP_TOKEN="Your Azure DevOps PAT" `
		-e AZP_AGENT_NAME="Your Agent Name" `
		-e AZP_POOL="Your Agent Pool Name"
	```

## Building Manually

1. Clone the repository:
	```sh
	git clone https://github.com/armorynode/azpalpineagent.git
	```
2. Navigate to project directory:
	```sh
	cd azpalpineagent
	```
3. Build Docker image:
	```sh
	docker build -t azpalpineagent:latest .
	```
4. Run the Docker container:
    ```sh
	# Linux/MacOS
    docker run -d ghcr.io/armorynode/azpalpineagent:main \
		-e AZP_URL="Your DevOps Organization URL" \
		-e AZP_TOKEN="Your Azure DevOps PAT" \
		-e AZP_AGENT_NAME="Your Agent Name" \
		-e AZP_POOL="Your Agent Pool Name"
    ```

	```PowerShell
	# Windows
	docker run -d ghcr.io/armorynode/azpalpineagent:main `
		-e AZP_URL="Your DevOps Organization URL" `
		-e AZP_TOKEN="Your Azure DevOps PAT" `
		-e AZP_AGENT_NAME="Your Agent Name" `
		-e AZP_POOL="Your Agent Pool Name"
	```

## Using Docker Compose

1. Create a `compose.yml` file in your project directory with the following content:
	```yml
	version: '3.8'

	services:
	agent1:
	  image: ghcr.io/armorynode/azpalpineagent:main
	  ports:
	    - "8081:80"
	  environment:
	    - AZP_URL=Your DevOps Organization URL
	    - AZP_TOKEN=Your Azure DevOps PAT
	    - AZP_AGENT_NAME=Agent1
	    - AZP_POOL=Your Agent Pool Name
 
	agent2:
	  image: ghcr.io/armorynode/azpalpineagent:main
	  ports:
	    - "8082:80"
	  environment:
	    - AZP_URL=Your DevOps Organization URL
	    - AZP_TOKEN=Your Azure DevOps PAT
	    - AZP_AGENT_NAME=Agent2
	    - AZP_POOL=Your Agent Pool Name

	agent3:
	  image: ghcr.io/armorynode/azpalpineagent:main
	  ports:
	    - "8083:80"
	  environment:
	    - AZP_URL=Your DevOps Organization URL
	    - AZP_TOKEN=Your Azure DevOps PAT
	    - AZP_AGENT_NAME=Agent3
	    - AZP_POOL=Your Agent Pool Name
	```

2. Start the Docker Compose services:
	```sh
	docker-compose up -d
	```

This will start three instances of the azpalpineagent container, each accessible on different ports (8081, 8082, and 8083).
