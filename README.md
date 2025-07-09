
# Cloud Development Demo - DevSpace Setup

This branch demonstrates how to develop and run the **Cloud development demo** SpringBoot application connected to PostgreSQL using [DevSpace](https://devspace.sh/) in a Kubernetes cluster.

---

## Prerequisites

- Kubernetes cluster access and `kubectl` configured to interact with the cluster
- [DevSpace CLI](https://devspace.sh/cli) installed locally
- [Helm](https://helm.sh/) installed for managing the PostgreSQL deployment
- Git installed

---

## Setup and Run

### 1. Clone the repository and checkout this branch

```bash
git clone https://github.com/lvoss/cloud-development-demo.git
cd cloud-development-demo
git checkout env-devspace
```

### 2. Select your Kubernetes namespace

Connect your `kubectl` to the desired Kubernetes cluster and choose the namespace where you want to deploy the application:

```bash
devspace use namespace <my-namespace>
```

Replace `<my-namespace>` with your target namespace. This step ensures subsequent commands operate against the right namespace.

### 3. Deploy the application and PostgreSQL database

PostgreSQL is deployed using Helm as part of the setup. Deploy the app and the database with:

```bash
devspace deploy
```

This command deploys all components defined in the `devspace.yaml` including Helm-based Postgres.

### 4. Start the development environment

Launch a development session that forwards the application ports and syncs your local source code into the Kubernetes pod:

```bash
devspace dev
```

- The SpringBoot app will be running inside a pod in your cluster.
- Your local code edits are actively synchronized into the pod.
- Application ports are forwarded locally so you can access the app on your machine.
- You can set breakpoints if using a remote debugger configured with DevSpace.

---

## Verifying the Application

Once `devspace dev` is running:

- The application listens on port 8080.
- Open your browser and navigate to:

```bash
http://localhost:8080/
```

- You should see the message:

```bash
Up and running!
```

This confirms a successful connection between the SpringBoot app and the deployed PostgreSQL database.

---

## Development Workflow

- Make changes to your source code locally. DevSpace auto-syncs changes into the pod.
- Restart the SpringBoot app inside the pod if needed (e.g., via remote shell or remote debug tooling).
- Logs and debugging information are available via `devspace logs` or through your IDE.
- Ports are forwarded automatically during `devspace dev`.
- You can set remote debug breakpoints as supported by your IDE and DevSpace configuration.

---

## Troubleshooting

- Ensure your Kubernetes context and namespace are correct (`kubectl config current-context` and `kubectl get namespaces`).
- Confirm Helm installed the Postgres release successfully (`helm list`).
- If the app fails to start or connect to the database, check logs:

```bash
devspace logs <pod-name>
```

- Verify your local ports are correctly forwarded by DevSpace.
- Check that the environment variable `DATASOURCE_URL` matches your database connection string.

---

## Useful Commands

| Purpose                  | Command                                           |
|--------------------------|--------------------------------------------------|
| Switch namespace         | `devspace use namespace <my-namespace>`           |
| Deploy app and DB        | `devspace deploy`                                 |
| Start development mode   | `devspace dev`                                    |
| View logs                | `devspace logs <pod-name>`                        |
| List pods                | `kubectl get pods -n <my-namespace>`             |
| Stop development mode    | `CTRL+C` in terminal running `devspace dev`      |

---

## Configuration Details

- PostgreSQL is deployed via Helm as part of the devspace workflow.
- Application connects to Postgres using a fixed user and password configured in the `DATASOURCE_URL` environment variable.
- All Kubernetes and DevSpace config is managed in the `devspace.yaml` file.

---

## Additional Resources

- [DevSpace Official Documentation](https://devspace.sh/docs)
- [Helm Package Manager](https://helm.sh/)
- [Kubernetes Documentation](https://kubernetes.io/docs/home/)
- [Spring Boot Reference Guide](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/)
- [PostgreSQL Docker Image](https://hub.docker.com/_/postgres)
