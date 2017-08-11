The Rodin's Node.js docker image.

## What is Node.js?

Node.js is a platform built on Chrome's JavaScript runtime for easily building
fast, scalable network applications. Node.js uses an event-driven, non-blocking
I/O model that makes it lightweight and efficient, perfect for data-intensive
real-time applications that run across distributed devices.

See: http://nodejs.org

# How to use this image

## Create a `Dockerfile` in your Node.js app project

```dockerfile
# specify the node base image with your desired version node:<version>
FROM node:6
# replace this with your application's default port
EXPOSE 8888
```

You can then build and run the Docker image:

```console
$ docker build -t my-nodejs-app .
$ docker run -it --rm --name my-running-app my-nodejs-app
```

If you prefer Docker Compose:

```yaml
version: "2"
services:
  node:
    image: "node:8"
    environment:
      - NODE_ENV=production
    volumes:
      - ./:/usr/src/app
    expose:
      - "8080"
```

You can then run using Docker Compose:

```console
$ docker-compose up -d
```

### Notes

The image assumes that your application has a file named
[`package.json`](https://docs.npmjs.com/files/package.json) listing its
dependencies and defining its [start
script](https://docs.npmjs.com/misc/scripts#default-values).

It also assumes that you have a file named [`.dockerignore`](https://docs.docker.com/engine/reference/builder/#/dockerignore-file) otherwise it will copy your local npm modules:

```
node_modules
```# Docker-NodeJS-alpine
Rodin Docker Image for Node.js
