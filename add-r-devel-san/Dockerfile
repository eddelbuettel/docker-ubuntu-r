## Emacs, make this -*- mode: sh; -*-

## start with the Ubuntu docker-ubuntu-r/add-r which has R on top of the latest Ubuntu
FROM eddelbuettel/docker-ubuntu-r:add-r

## That's me
MAINTAINER Dirk Eddelbuettel edd@debian.org

## Remain current
RUN apt-get update -qq
RUN apt-get dist-upgrade -y

## From the Build-Depends of the Debian R package, plus subversion
RUN apt-get install -y --no-install-recommends gcc g++ gfortran gcc-4.8 g++-4.8 gfortran-4.8 libblas-dev liblapack-dev tcl8.5-dev tk8.5-dev bison groff-base libncurses5-dev libreadline-dev debhelper texinfo libbz2-dev liblzma-dev libpcre3-dev xdg-utils zlib1g-dev libpng-dev libjpeg-dev libx11-dev libxt-dev x11proto-core-dev libpango1.0-dev libcairo2-dev libtiff5-dev xvfb xauth xfonts-base texlive-base texlive-latex-base texlive-generic-recommended texlive-fonts-recommended texlive-fonts-extra texlive-extra-utils texlive-latex-recommended texlive-latex-extra default-jdk mpack bash-completion subversion 
## broken with clamg-3.5:
##  clang -std=gnu99 -fsanitize=undefined -fno-omit-frame-pointer -shared -L/usr/local/lib -o libRblas.so blas.o  cmplxblas.o -lgfortran -lm -lquadmath # xerbla.o
##  /usr/bin/ld: /usr/bin/../lib/clang/3.5/lib/linux/libclang_rt.san-x86_64.a(sanitizer_tls_get_addr.o): relocation R_X86_64_TPOFF32 against `_ZN11__sanitizerL4dtlsE' can not be used when making a shared object; recompile with -fPIC
##  /usr/bin/../lib/clang/3.5/lib/linux/libclang_rt.san-x86_64.a(sanitizer_tls_get_addr.o): error adding symbols: Bad value
##  clang: error: linker command failed with exit code 1 (use -v to see invocation)


## Check out R-devel
RUN cd /tmp && svn co http://svn.r-project.org/R/trunk R-devel 

## Build and install
##RUN cd /tmp/R-devel && R_PAPERSIZE=letter R_BATCHSAVE="--no-save --no-restore" R_BROWSER=xdg-open PAGER=/usr/bin/pager PERL=/usr/bin/perl R_UNZIPCMD=/usr/bin/unzip R_ZIPCMD=/usr/bin/zip R_PRINTCMD=/usr/bin/lpr LIBnn=lib AWK=/usr/bin/awk CFLAGS="-pipe -std=gnu99 -Wall -pedantic -O2 -fno-omit-frame-pointer -g" CXXFLAGS="-pipe -Wall -pedantic -O3" CC="clang -fsanitize=alignment,array-bounds,bool,enum,float-cast-overflow,float-divide-by-zero,function,integer-divide-by-zero,null,object-size,return,shift,signed-integer-overflow,unreachable,vla-bound,vptr" CXX="clang++ -fsanitize=alignment,array-bounds,bool,enum,float-cast-overflow,float-divide-by-zero,function,integer-divide-by-zero,null,object-size,return,shift,signed-integer-overflow,unreachable,vla-bound,vptr" FC="gfortran" F77="gfortran" ./configure --enable-R-shlib --without-blas --without-lapack --without-readline --without-recommended-packages --program-suffix=dev
RUN cd /tmp/R-devel && R_PAPERSIZE=letter R_BATCHSAVE="--no-save --no-restore" R_BROWSER=xdg-open PAGER=/usr/bin/pager PERL=/usr/bin/perl R_UNZIPCMD=/usr/bin/unzip R_ZIPCMD=/usr/bin/zip R_PRINTCMD=/usr/bin/lpr LIBnn=lib AWK=/usr/bin/awk CFLAGS="-pipe -std=gnu99 -Wall -pedantic -O2 -fno-omit-frame-pointer -g" CXXFLAGS="-pipe -Wall -pedantic -O3" CC="gcc-4.8 -fsanitize=address" CXX="g++-4.8 -fsanitize=address" FC="gfortran-4.8 -fsanitize=address" F77="gfortran-4.8 -fsanitize=address" ./configure --enable-R-shlib --without-blas --without-lapack --without-readline --without-recommended-packages --program-suffix=dev
RUN cd /tmp/R-devel && make && make install

## Set Renviron.site to get libs from base R install
run echo "R_LIBS_SITE=\${R_LIBS_SITE-'/usr/local/lib/R/site-library:/usr/local/lib/R/library:/usr/lib/R/library'}" > /usr/local/lib/R/etc/Renviron.site
run cd /usr/local/bin && mv R Rdevel && mv Rscript Rscriptdevel

