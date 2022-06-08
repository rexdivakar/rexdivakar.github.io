---
title: A beginner’s guide to Docker  --  how to create your first Docker application 🐳
author: rexdivakar
date: 2022-06-07 07:47:00
categories: [containers, docker]
tags: [docker, docker-compose, containers]
math: true
mermaid: true
toc: true # table of contents
comments: true
pin: false
---

![docker]({{"/assets/img/dock_fish.jpg"| absolute_url}}){: width="600" height="600" }{: .shadow }

Before starting to build the app, lets first install the pre requisites for building the docker container,

## 1. Install Docker on your machine

> For Linux (Ubuntu/Debian Based distros):

```shell
sudo apt install docker.io
```

For MacOSX: you can follow this [link](https://docs.docker.com/desktop/windows/install/) <br />
For Windows: you can follow this [link](https://docs.docker.com/desktop/mac/install/) <br />

> For Windows (Enable WSL2 backend for optimized performance)

### Finally, verify that Docker is installed correctly

```shell
sudo docker run hello-world
```

## 2. Create your project

Create a new directory and two files main.py and Dockerfile.

* main.py -- contains python code for web server.
* Dockerfile -- this file contains the structure of container.
* requirements.txt -- this is a dependency file for python web server(flask).

Kindly add this code to your main.py to initiate web server,

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
 return 'Hello World'


if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0', port=5000)

```

add the below dependency to requirements.txt file,

```text
Flask==2.1.2
```

## 3. Edit the Docker file

The first step to take when you create a Docker file is to access the DockerHub website. This site contains many pre-designed images to save your time (for example: all images for linux or code languages).

In our case, we will type ‘Python’ in the search bar. The first result is the official image created to execute Python. Perfect, we’ll use it!

```Dockerfile
# start by pulling the python image
FROM python:3.8-alpine

# copy the requirements file into the image
COPY ./requirements.txt /app/requirements.txt

# switch working directory
WORKDIR /app

# install the dependencies and packages in the requirements file
RUN pip install -r requirements.txt

# copy every content from the local file to the image
COPY . /app

# configure the container to run in an executed manner
ENTRYPOINT [ "python" ]

CMD ["main.py" ]
```

### Let’s go over the instructions in this Dockerfile

**FROM python:3.8-alpine**: Since Docker allows us to inherit existing images, we install a Python image and install it in our Docker image. Alpine is a lightweight Linux distro that will serve as the OS on which we install our image

**COPY  ./requirements.txt /app/requirements.txt**: Here, we copy the requirements file and its content (the generated packages and dependencies) into the app folder of the image

**WORKDIR  /app**: We proceed to set the working directory as /app, which will be the root directory of our application in the container
**RUN pip install -r requirements.txt**: This command installs all the dependencies defined in the requirements.txt file into our application within the container

**COPY  . /app**: This copies every other file and its respective contents into the app folder that is the root directory of our application within the container

**ENTRYPOINT [ "python" ]**: This is the command that runs the application in the container

**CMD [ "main.py" ]**: Finally, this appends the list of parameters to the EntryPoint parameter to perform the command that runs the application. This is similar to how you would run the Python app on your terminal using the python main.py command.

## 4. Build the Docker image

Let’s proceed to build the image with the command below:

```shell
docker image build -t flask_docker .
```

## 5. Run the container

After successfully building the image, the next step is to run an instance of the image. Here is how to perform this:

```shell
docker run -p 5000:5000 -d --name new_app flask_docker
```

This command deploys the container with the python flask server running on port 5000, Here is the output of our application when we send a request to localhost:5000 on our browser,

![docker-output]({{"/assets/img/op.png"| absolute_url}}){: width="600" height="600" }{: .shadow }

### Track the container status

The below command displays the list of all running active containers, check if your deployed container is in running status!

```shell
docker ps -a
```

## 6. Useful commands for Docker

> ### List your images

```shell
docker images
```

> ### Delete a specific image

```shell
docker image rm [image name]
```

> ### List all existing containers (running and not running)

```shell
docker ps -a
```

> ### Stop a specific container

```shell
docker stop [container name]
```

> ### Delete a specific container

```shell
docker rm [container name]
```

> ### Display logs of a container

```shell
docker logs [container name]
```

> Note: If you want to learn more about Dockerfiles, check out [Best practices for writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/).
{: .prompt-info }

## 7. Conclusion

In this article, we built a simple Flask app and containerized it with Docker. You can refer to this post every time you need a simple and concrete example on how to create your first Docker application. If you have any questions or feedback, feel free to ask.
