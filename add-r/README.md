
## Docker Images for R on Ubuntu

These directories offer several configurations for R on Ubuntu:

* `add-r`: Starts from `ubuntu:latest` and adds just the R binary via the
r-base package, as well as littler.  This images carries the default tag `latest`.

* `add-r-devel`: Starts from `latest` and adds all Build-Depends: for the R
package as well as subversion; it checks out the current SVN sources of
R-devel, and then builds R-devel which is installed as
`/usr/local/bin/Rdevel` to distinguish from `R` which invokes the released version of R.
This image is installed with tag `add-r-devel`.

## GitHub repo

See [the GitHub repo](https://github.com/eddelbuettel/docker-ubuntu-r) for
sources etc.

### Docker Hub

The GitHub  repository is linked to 
[this automated build facility at Docker](https://registry.hub.docker.com/u/eddelbuettel/docker-ubuntu-r/)
and one can retrieve the corresponding images via a standard `docker pull`.

### Author

Dirk Eddelbuettel

### License

GPL (>= 2)



