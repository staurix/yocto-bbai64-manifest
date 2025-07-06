# yocto-bbai64-manifest

Yocto layer `repo` manifest for [BeagleBone AI-64](https://www.beagleboard.org/boards/beaglebone-ai-64).

This project aims to produce a bootable Yocto image using the `Arago` distro.

## Install `repo` tool

Official documentation can be found [here](https://gerrit.googlesource.com/git-repo/+/HEAD/README.md).

``` bash
mkdir -p ~/bin
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```

## Initialize the Yocto source directory

``` bash
repo init -u https://github.com/staurix/yocto-bbai64-manifest.git -b scarthgap
repo sync
```

## Bitbake

### Notes

Even though this project has been created around `BeagleBone AI-64`, it can potentially be used for many other TI machines.

List of `TI` machines:

``` bash
layers/meta-ti/meta-ti-bsp/conf/machine
```

List of `BeagleBone` machines:

``` bash
layers/meta-ti/meta-beagle/conf/machine
```

In this case, the `beaglebone-ai64` machine is used:

``` bash
MACHINE ??= "beaglebone-ai64"
```

### Source the build environment

``` bash
source layers/poky/oe-init-build-env builds/build-BBAI64
```

### Build the image

List of `Texas Instruments` images:

``` bash
layers/meta-arago/meta-arago-distro/recipes-core/images
```

Mainly:
- tisdk-base-image
- tisdk-default-image

``` bash
bitbake tisdk-default-image
```

`Note`: If the compilation freezes/fails, consider using `BB_NUMBER_THREADS` and `PARALLEL_MAKE`.

## Useful links

- [Yocto BeagleBone AI-64 manifest repo](https://github.com/saizen408/bbai64-repo-manifest)
- [Yocto #5 (GUI linux image using arago)](https://www.youtube.com/watch?v=pD3prnBSC5s)

## License

This project is licensed under the MIT License. For more details, please refer to the [LICENSE](LICENSE) file.

## Copyright

Copyright &copy; 2025 staurix &reg;, All rights reserved.

<!-- End of file -->
