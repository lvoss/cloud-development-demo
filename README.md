
# Cloud Development Demo - OpenShift DevSpaces Setup

This branch demonstrates how to develop and run the **Cloud development demo** SpringBoot application connected to PostgreSQL using **OpenShift DevSpaces**.

---

## Prerequisites

- Access to an OpenShift cluster with OpenShift DevSpaces enabled
- OpenShift CLI (`oc`) installed and configured to connect to your cluster
- Git installed on your local machine
- Basic familiarity with OpenShift DevSpaces concepts

---

## Setup and Run

### 1. Log in to your OpenShift cluster and open the github project OpenShift DevSpaces

- In the OpenShift console, create or open a DevSpaces environment for this project.
- Alternatively, from the CLI, launch the workspace you have configured for this branch.
- Using the github url of this repository/branch (`https://github.com/lvoss/cloud-development-demo/tree/env-openshift-devspaces`), start an OpenShift DevSpace.

### 2. Start the SpringBoot application inside OpenShift DevSpaces workspace

- Inside your OpenShift DevSpaces workspace terminal, run:

```bash
./mvnw spring-boot:run
```

- This will start the application on port `8080` inside the workspace.

### 3. Verify the application

- Access the provided url on startup (or look up the Route within the associated OpenShift project) to access the application.

```bash
https://<openshift-devspaces-url>
```

- You should see:

```bash
Up and running!
```

which confirms the SpringBoot app is running and connected to the PostgreSQL database.

---

## Development Workflow

- Source code changes you make within your DevSpaces workspace are immediately available inside the container.
- Restart the SpringBoot app by stopping (`CTRL+C`) and rerunning the `./mvnw spring-boot:run` command.
- You can set breakpoints and debug the application from within the IDE that is running in the OpenShift cluster / your browser.

---

## Troubleshooting

- Validate your OpenShift login and permissions if deployments fail.
- Inspect logs for the SpringBoot app pod or OpenShift Devspaces terminal.
- Confirm the environment variable `DATASOURCE_URL` matches the deployed Postgres connection info.

---

## Useful Commands

| Purpose                      | Command / Notes                                           |
|------------------------------|-----------------------------------------------------------|
| Log in to OpenShift          | `oc login <api-server> --token=<token>`                  |
| Start SpringBoot application | `./mvnw spring-boot:run`                                 |
| Stop SpringBoot application  | `CTRL+C` in terminal                                      |
| Check logs                   | Use `oc logs <pod-name>` or workspace terminal           |

---

## Configuration Details

- The application connects to Postgres with fixed credentials via the environment variable `DATASOURCE_URL`.
- OpenShift DevSpaces will leverage configuration files in this branch (`devfile.yaml` manifests and Helm charts) to deploy both PostgreSQL and the SpringBoot app.
- When your OpenShift DevSpaces environment starts, it will automatically deploy the PostgreSQL database as a second container within the development Pod.
- The SpringBoot app will connect to Postgres using a predefined username, password, and the `DATASOURCE_URL` environment variable.

---

## Additional Resources

- [OpenShift DevSpaces Documentation](https://www.openshift.com/devspaces)
- [OpenShift CLI (`oc`) Documentation](https://docs.openshift.com/container-platform/latest/cli_reference/openshift_cli/getting-started-cli.html)
- [Helm Package Manager](https://helm.sh/)
- [Spring Boot Reference Guide](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/)
- [PostgreSQL Docker Image](https://hub.docker.com/_/postgres)
