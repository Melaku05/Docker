# Docker
`A platform for building, running and shipping applications`
## Reasons we should use docker

- One or more files missing
- Software version mismatch
- Different configurations settings 
## Container
`An isolated environment for running an application`
-  Allow running multiple apps in isolation
- Are lightweight
- use os of the host
- start quickly
- need less hardware resources 

## Architecture of docker
- client(container) ---> api(docker engine)
-container is just a process like other process runing on your computer
- All Container in the host share the operating system of the host

# anyfile(project)--> dockerfile--->image
## Image contain
- A cut-down os
- A runtime environment (eg node)
- Application files
- Third-party libraries
- Environment varibales

## dockerize the project by add dockerfile which is contain all thing to convert to image 

## dev(image)--->docker hub(registry) anyone can use it---> test/prod


## Instructions
- start with an Os
- Install Node
- Copy app files
- Run node app.js


# you can take any application and dockerized it by adding Dockerfile to it, this docker file contain instruction for packaing an application into an image, once we have an image we can run it virtual anywere.
