Alpine GNU C library (glibc) Docker image
=========================================

This image is based on Alpine Linux image, which is only a 5MB image, and contains glibc to enable
proprietary projects compiled against glibc (e.g. OracleJDK, Anaconda) work on Alpine.

This image includes some quirks to make [glibc](https://www.gnu.org/software/libc/) work side by
side with musl libc (default in Alpine Linux). glibc packages for Alpine Linux are prepared by
[Sasha Gerrand](https://github.com/sgerrand) and the releases are published in
[sgerrand/alpine-pkg-glibc](https://github.com/sgerrand/alpine-pkg-glibc) github repo.

If you need to update your libc library cache, use `/usr/glibc-compat/sbin/ldconfig` instead of the usual `/sbin/ldconfig`. You can also use the `LD_LIBRARY_PATH` as on standard libc-based distributions.

Usage Example
-------------

This image is intended to be a base image for your projects, so you may use it like this:

```Dockerfile
FROM michaelcoll/alpine-glibc

COPY ./my_app /usr/local/bin/my_app
```

```sh
$ docker build -t my_app .
```
