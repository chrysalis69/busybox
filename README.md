# Busybox


This docker images contains to bare requirements of a busybox environment that can run oracle java.

Other images will be based on this image.

## Getting Started

```
docker build -t chrysalis:busybox-builder --pull -f Dockerfile.builder busybox
docker run --rm chrysalis:busybox-builder tar cC rootfs . | xz -z9 > "busybox.tar.xz"
docker build -t chrysalis:busybox busybox
```

Building this image is a multistep process.
First we need to build the root of our busybox docker image using a debian jessie image.
We'll use this container to install all the required development tools, and build our busybox root.
We'll also inject a few extra files, like libnss, libpthread, libdl and all their dependencies.

After that is done, we create a docker image and inject the root created in the first image


