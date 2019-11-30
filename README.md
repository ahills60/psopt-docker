# PSOPT in Docker

PSOPT in Docker is a container that contains the [PSOPT](https://github.com/PSOPT/psopt) optimisation tool environment. This recreates the development environment required to build PSOPT and its examples. This DockerFile is maintained on GitHub at [`ahills60/psopt-docker`](https://github.com/ahills60/psopt-docker).

## Build notes

Building PSOPT within Docker requires additional memory resource. This means that automated builds with DockerHub are prone to build failure due to [resource limitations](https://success.docker.com/article/docker-hub-automated-build-fails-and-the-logs-are-missing-empty) (this occurs in a `g++` call resulting in early termination of the process). For this reason, PSOPT containers are built locally and pushed to DockerHub. 

Recommended memory assignment:

* At least 4 GB of memory.
* At least 2 GB of swap.

## Binding

It is suggested that you create a mount point from your local machine to `/root/psopt`. This will provide access to all of the psopt source files and examples, enabling development to talk place within this area.

## Notes

This image uses the `root` user and is thus this comes with the caveat that this should not be deployed in secure environments without appropriate security considerations. It is also easy to destroy the environment. A workaround would be to create a new user and use this user to build within the PSOPT environment.