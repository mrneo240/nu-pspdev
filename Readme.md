# A Docker Image for PSP Development

[![](https://images.microbadger.com/badges/image/haydenkow/nu-pspdev.svg)](https://microbadger.com/images/haydenkow/nu-pspdev)
[![](https://img.shields.io/docker/pulls/haydenkow/nu-pspdev.svg?maxAge=604800)](https://hub.docker.com/r/haydenkow/nu-pspdev/)

Cross-compile your PSP homebrew projects inside a Docker container based on [psptoolchain](https://github.com/pspdev/psptoolchain).

## Quick Start

Run this command in your project's root folder to build it inside a Docker container:

```bash
docker run -it --rm -v "$PWD:/src" haydenkow/nu-pspdev make
```

This will mount the current folder to `/src` in the container and then run `make` inside `/src`. You may execute other commands, of course.

Omit the command to get a login shell (`/bin/bash`) in the running container:

```bash
docker run -it --rm -v "$PWD:/src" haydenkow/nu-pspdev
```

## Continuous Integration

With the Docker image in hand, you can also build and test your PSP applications on CI platforms. Here's an example configuration for Travis CI:

```yaml
# .travis.yml
language: c

sudo: required

services:
  - docker

script: docker run -it --rm -v "$PWD:/src" haydenkow/nu-pspdev make test
```

## Origin

This project is forked from [Mathias Lafeldt](https://twitter.com/mlafeldt)'s [docker-ps2dev](https://github.com/mlafeldt/docker-ps2dev).
