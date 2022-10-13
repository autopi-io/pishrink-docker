# PiShrink dockerized

**PiShrink** automatically shrink a Raspberry Pi image in order to reduce the final image size.

It's great for saving disk space or sharing your Pi image on the Internet.

This project is a dockerized version of the [PiShrink bash script](https://github.com/Drewsif/PiShrink) by Drew Bonasera.

![Release][release-install-shield] [![License][license-shield]](LICENSE.md)

# AutoPi Instructions.

## Building

Before you can use this tool, you need to build and tag the docker container with the following commands.
```bash
docker build . --tag autopi/pishrink:v1
```

## Usage

1. Using the Terminal, access the directory containing the Raspberry Pi image:

    ```bash
    cd ~/Directory-with-RPi-image
    ```

2. Run PiShrink dockerized:
    ```bash
    docker run --privileged=true --rm --volume $(pwd):/workdir autopi/pishrink:v1 pishrink -zpdv SOURCE_IMAGE.img OUTPUT_IMAGE.img
    ```

    Example
    ```bash
    docker run --privileged=true --rm --volume $(pwd):/workdir autopi/pishrink:v1 pishrink -zpdv autopi_core_tmu_260722_v1-22_prepared_TENANT.img autopi_core_tmu_260722_v1-22_prepared_SHRINKED.img
    ```
3. Now the output is shrinked and compressed, and can be used in the image build process.

## PiShrink options

```shell
pishrink [-adhrspvzZ] IMAGE.img NEW-IMAGE.img

-s      Do not expand filesystem when image is booted the first time
-v      Enables more verbose output
-r      Use advanced filesystem repair option if the normal one fails
-z      Compress image after shrinking with gzip
-Z      Compress image after shrinking with xz
-a      Compress image in parallel using multiple cores
-p      Remove logs, apt archives, dhcp leases and ssh hostkeys
-d      Write debug messages in a debug log file
```

If you specify the `NEW-IMAGE.img` parameter, the script will make a copy of `IMAGE.img` and work off that. You will need enough space to make a full copy of the image to use that option.

Check out [PiShrink GitHub](https://github.com/Drewsif/PiShrink) for more details.

## Docker Hub

* [mgomesborges/pishrink](https://hub.docker.com/r/mgomesborges/pishrink)

## Author

* [Marcos Gomes-Borges](https://github.com/mgomesborges)

## License

The source code is licensed under the [MIT license](LICENSE.md).

The content of this project itself is licensed under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0).

[release-install-shield]: https://img.shields.io/badge/Release-01--Nov--2021-blue
[license-shield]: https://img.shields.io/github/license/mgomesborges/mac-dev-setup.svg
