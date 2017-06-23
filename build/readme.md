# Building Images

This project uses custom Docker images, hosted at [https://hub.docker.com/r/smachara2/cumulus-repositoty/](https://hub.docker.com/r/smachara2/cumulus-repositoty/).

These images are built here ahead of time using the `build` bash script found in this directory.

## Usage

The usage of the `build` script is:

```bash
# Log into the smachara2 Docker Hub user
$ docker login

# Build a new version
$ ./build 1.1
```

## Explanation

This build script pushes up to the `smachara2` repository, so only I can actually push to it.

However it's useful to see how you might use it to build your own images (simply replace the `smachara2` namespace with your own).

Let's see an example, with comments to explain what we're doing:

```bash
# Log into your Docker Hub account
$ docker login

# Find our build files
$ cd cumulus-repositoty/build

# Build an Gitlab image with your own namespace
# We tag is 1.0 and latest - you can tag it any version
#  in addition to tagging it the "latest"
$ docker build -t your-namespace/gitlab:1.0 -t your-namespace/gitlab:latest

# Push both images up
$ docker push your-namespace/gitlab:1.0
$ docker push your-namespace/gitlab:latest
```