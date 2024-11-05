[![Build and Push Docker Image](https://github.com/bwbioinfo/slow5tools-docker-cwl/actions/workflows/build-and-push.yml/badge.svg)](https://github.com/bwbioinfo/slow5tools-docker-cwl/actions/workflows/build-and-push.yml)

# slow5tools-docker-cwl

This repository provides a [Common Workflow Language (CWL)](https://www.commonwl.org/) tool for running the [Slow5Tools](https://github.com/hasindu2008/slow5tools) program. The tool is packaged in a Docker container, allowing it to run on any system with Docker or Singularity installed.

## Prerequisites

To use this tool, you must have the following software installed on your system:

- [CWL tool](https://github.com/common-workflow-language/cwltool)
- [Docker](https://www.docker.com/) OR [Singularity](https://sylabs.io/singularity/) OR [Apptainer](https://apptainer.org/)

## Installation

To install and run the tool, follow these steps:

1. Clone this repository to your local machine.
2. Install Docker, if you haven't already done so.
3. (Optional) Build the Docker image by running the following command from the root of the repository:

    ```bash
    docker build -f docker/Dockerfile -t slow5tools-docker-cwl .
    ```
    OR pull the pre-built container:

    ```bash
    docker pull ghcr.io/bwbioinfo/slow5tools-docker-cwl:latest
    ```

   **Note**: Building the image is only needed if you wish to access the container commands directly via Docker.

4. Run the CWL tool with the following command from the root of the repository:

    ```bash
    cwl-runner slow5tools-tool.cwl slow5tools-inputs.yml
    ```
    OR with Singularity:

    ```bash
    cwl-runner --singularity slow5tools-tool.cwl slow5tools-inputs.yml
    ```

   This will run Slow5Tools on the input specified in the `slow5tools-inputs.yml` file.

## Usage

To use the tool, create a YAML file specifying the input file and any other parameters. An example YAML file is provided in the `example` directory of this repository.

- **`slow5tools-tool.cwl`**: The main workflow file that defines the steps for the Slow5Tools analysis.
- **`slow5tools-inputs.yml`**: An example input file that specifies the input data and any other options.

The output of the analysis will be written to a directory named `output` in the current working directory.

## Contributing

If you wish to contribute to this project, please follow the standard GitHub workflow:

1. Fork the repository
2. Create a new branch for your changes
3. Make your changes and commit them
4. Push your changes to your fork
5. Submit a pull request to this repository

## License

This project is licensed under the [MIT License](https://github.com/bwbioinfo/slow5tools-docker-cwl/blob/main/LICENSE).

## Contact

If you have any questions or feedback, please contact the author via GitHub.
