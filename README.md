# Requirements

- LXD >= 4.0
- Distrobuilder >= 2.0

# Required packages

- Packages : debootstrap - qemu-utils - zstd

```shell
$ sudo apt install -y debootstrap qemu-utils zstd
```

# How to build these images ?

Firstly, install `distrobuilder` using `snap` :

```shell
$ snap install distrobuilder --classic
```

Then, build the image using `distrobuilder` (and import it directly) :

* **Container image**

  ```shell
  $ distrobuilder build-lxd fedora/default.yml --type=unified --compression=zstd --import-into-lxd=<image alias>
  ```

* **Virtual machine image**

  ```shell
  $ distrobuilder build-lxd ubuntu/default.yml --type=unified --compression=zstd --vm --import-into-lxd=<image alias>
  ```

You can also specify a distribution release version or architecture with the `-o image.*` flag :

  ```shell
  $ distrobuilder build-lxd fedora/default.yml -o image.release=35 [options]
  $ distrobuilder build-lxd ubuntu/default.yml -o image.release=impish -o image.architecture=arm64 [options]
  ```