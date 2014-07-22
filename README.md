
## Docker for R on Ubuntu

This repository contains Dockerfiles defining images which extend the default
Ubuntu image for Docker. The aim is on making R development and testing easier.

### Docker Images

We start from the latest Ubuntu release and then add:

* add-r:  This image adds just the R executable. Other images below depend on it.
* add-r-devel: This image adds a freshly-built R-devel version, as well as
all tools required to build R-devel from source.

### Docker Hub

This repository is linked to 
[this automated build facility at Docker](https://registry.hub.docker.com/u/eddelbuettel/docker-ubuntu-r/)
and one can retrieve the corresponding images via a standard `docker pull`.

#### Open build issues

* We are testing these on the inofficial i386 variant where the fuller
specification create files that are larger than 2gb wh

### Author

Dirk Eddelbuettel

### License

GPL (>= 2)

