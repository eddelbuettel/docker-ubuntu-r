
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

### See Also

There is a corresponding 
[Docker for R on Debian repo](https://github.com/eddelbuettel/docker-debian-r) 
I also maintain which has a few more builds.

### Author

Dirk Eddelbuettel

### License

GPL (>= 2)

