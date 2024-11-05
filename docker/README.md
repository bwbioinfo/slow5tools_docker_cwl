# Dockerfile for Slow5Tools

This repository provides a Docker setup for [Slow5Tools](https://github.com/hasindu2008/slow5tools), a tool for efficiently handling raw nanopore sequencing data in the SLOW5 format. The Docker image is based on a minimal Alpine Linux setup to keep the image size small while including all necessary dependencies for building and running Slow5Tools.

## Docker Image Overview

- **Base Image**: Alpine Linux (latest)
- **Dependencies**:
  - `bash`: For shell scripting and compatibility
  - `curl`: For downloading files
  - `hdf5-dev`, `zlib-dev`, `musl-dev`, `gcc`, `build-base`: Required libraries and build tools for compiling Slow5Tools
- **Slow5Tools Version**: Configurable as a build argument (`VERSION`), with a default value of `v1.3.0`.

## Dockerfile Instructions

The Dockerfile performs the following steps:

1. **Base Image Setup**: Starts from the latest Alpine Linux image.
2. **Install Packages**: Installs necessary packages (`bash`, `curl`, `hdf5-dev`, `zlib-dev`, etc.) in a single step to minimize image layers.
3. **Download and Build Slow5Tools**: Downloads the specified version of Slow5Tools from the GitHub releases page, extracts it, and compiles it.
4. **Cleanup**: Removes unnecessary files after installation, including the downloaded archive and build files, to reduce the final image size.
5. **Default Command**: Sets `/usr/local/bin/slow5tools` as the default command, allowing the container to execute Slow5Tools directly upon startup.

## Usage

### Building the Image

To build the Docker image, use the following command, optionally specifying a version:

```bash
docker build -t slow5tools --build-arg VERSION=v1.3.0 .
