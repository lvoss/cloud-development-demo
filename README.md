# Cloud Development Demo

This is a simple SpringBoot project that connects to a PostgreSQL database on startup.

Different development environments are showcased in separate branches:

- [DevContainers setup](https://github.com/lvoss/cloud-development-demo/tree/env-devcontainers)
- [GitHub Codespaces setup](https://github.com/lvoss/cloud-development-demo/tree/env-codespaces)
- [DevSpace setup](https://github.com/lvoss/cloud-development-demo/tree/env-devspace)
- [OpenShift DevSpaces setup](https://github.com/lvoss/cloud-development-demo/tree/env-openshift-devspaces)

Please switch to the relevant branch for detailed setup and usage instructions.

## Overview

The project demonstrates how to develop and run a SpringBoot application that connects to a Postgres database. It includes multiple development environment setups, each showcased in a separate branch:

- **`main`**: Common source code for the SpringBoot application.
- **`env-devcontainers`**: Example setup using [DevContainers](https://containers.dev/) or GitHub Codespaces.
- **`env-devspace`**: Example setup using [DevSpace](https://devspace.sh/).
- **`env-openshift-devspaces`**: Example setup using [OpenShift DevSpaces](https://www.openshift.com/blog/introducing-openshift-devspaces).

## Getting Started

This SpringBoot app requires a running PostgreSQL database on startup. The provided branches include the necessary configuration and instructions to start the Postgres database using the relevant tool for the environment.

### Branch Instructions

- **`main`**  
  Contains only the SpringBoot source code. You will need to start a Postgres instance manually (e.g., via Docker or locally).

- **`env-devcontainers`**  
  Use this branch if you want to develop using DevContainers or GitHub Codespaces. It contains configuration files to automatically start a Postgres container and connect your app to it.

- **`env-devspace`**  
  This branch demonstrates how to use DevSpace to deploy and run both the SpringBoot application and the Postgres database inside a Kubernetes cluster.

- **`env-openshift-devspaces`**  
  Use this branch if you want to develop on OpenShift DevSpaces. It includes manifests and configuration to deploy the app and Postgres database in the OpenShift environment.

## Usage

1. Checkout the branch corresponding to your chosen development environment.
2. Follow the instructions in the README or documentation found in that branch to get the Postgres database running.
3. Start the SpringBoot application, which will connect to the running Postgres database automatically.

## Requirements

- Docker (for `env-devcontainers` when using Devcontainers)
- Kubernetes / OpenShift cluster (for `env-devspace` and `env-openshift-devspaces` branches)
