# Prerequisites

{% include "../.gitbook/includes/docker-prerequisites.md" %}

# Steps to Run <code class="expression">space.vars.SITENAME</code>

{% include "../.gitbook/includes/oim-docker-configurations.md" %}

## Run Docker Container

- An image name is required to run docker container. Docker images need to be downloaded from the shared installer link.
- Pull/Load the image into local docker environment:
  ```bash
  docker load --input <Image_tar_filename>
  ```
- After updating Input.json and docker-compose-OIM.yml, run following command to start (up) the container:
  ```bash
  docker-compose -f docker-compose-OIM.yml up
  ```
- `-d` can also be added as an option to start docker container in detached mode.

# Known Limitations
{% include "../.gitbook/includes/docker-limitations.md" %}

# Upgrade Application Version

- Pull the image into local docker environment:
  ```bash
  docker load --input <Image_tar_filename>
  ```

{% include "../.gitbook/includes/docker-update-oim.md" %}

- To upgrade the application version, run the following command:
  ```bash
  docker-compose -f docker-compose-OIM.yml up
  ```




