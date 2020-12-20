[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/dgokcin/petsc4py/ci?&logo=github-actions)](https://github.com/dgokcin/petsc4py/actions)
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/dgokcin/petsc4py?logo=github)](https://github.com/dgokcin/petsc4py/releases)
[![Docker Image Version (latest semver)](https://img.shields.io/docker/v/denizgokcin/petsc4py?logo=docker&sort=semver)](https://hub.docker.com/repository/docker/denizgokcin/petsc4py/tags?page=1&ordering=last_updated)
[![Docker Image Size (latest semver)](https://img.shields.io/docker/image-size/denizgokcin/petsc4py?logo=docker&sort=semver)]()
[![Docker Pulls](https://img.shields.io/docker/pulls/denizgokcin/petsc4py?logo=docker)]()

### Description 
A Dockerized environment with petsc and its python dependencies bundled
together.

### Usage
![](doc/usage.gif)
### Changelog

| Image Tag | Image Size | Description                                        |
|-----------|--------|--------------------------------------------------------|
| v0.0.4    | 547MB  |changed the base image from debian slim to alpine 3.12  |
| v0.0.3    | 1.78GB |changed the base image from ubuntu 20.04 to debian-slim |
| v0.0.2    | 1.77GB |changed theentrypoint to the container for easier use   |
| v0.0.1    | 1.77GB |initial setup, bundled  all the  dependencies of  petsc |

### To run a custom python script inside the current directory with specific number of CPUs

- The command below mounts the current directory to the /home/petsc4py/app in
  the container, so make sure that you have your files in the current directory.
- Make sure that you enabled file sharing between the docker host and the images

```sh
docker run -it --rm -v ${PWD}:/home/petsc4py/app --cpus <CPU_COUNT> denizgokcin/petsc4py:<VERSION_NUMBER>
cd test_files
python3 customScript.py
```

### To build PETSc image

```sh
docker build -t petsc4py .
```

### To extend the docker image

```dockerfile
FROM denizgokcin/petsc4py:<TAG_NAME>

RUN apt-get update \
  && apt-get install -y \
    curl \
    vim

RUN pip3 install \
    h5py \
    pandas
```
