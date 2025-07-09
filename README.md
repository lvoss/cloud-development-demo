# Cloud Development Demo - DevContainers Setup

This branch demonstrates how to develop and run the **Cloud development demo** SpringBoot application connected to PostgreSQL using **DevContainers** with Visual Studio Code.

---

## Prerequisites

- [Visual Studio Code](https://code.visualstudio.com/) installed
- [Remote - Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) installed in VS Code
- Docker installed and running on your machine
- Git installed

---

## Setup and Run

### 1. Clone the repository and checkout this branch

```bash
git clone https://github.com/lvoss/cloud-development-demo.git
cd cloud-development-demo
git checkout env-devcontainers
```

### 2. Open the project in Visual Studio Code

- Launch VS Code
- Open the cloned folder (`cloud-development-demo`)
- Press `CMD+SHIFT+P` (or `CTRL+SHIFT+P` on Windows/Linux) to open the Command Palette
- Type **Remote-Containers: Reopen in Container** and select it

VS Code will now build the devcontainer environment, which includes Java 17. During this process, Docker Compose is automatically run to start a PostgreSQL container as a service, configured by `.devcontainer/docker-compose.yaml` in the branch.

### 3. Start the SpringBoot application

Once the devcontainer is up and running and you have a terminal inside the container:

```bash
./mvnw spring-boot:run
```

This will start the SpringBoot application on port `8080`.

### 4. Verify the application

Open your browser and navigate to:

```bash
http://localhost:8080/
```

You should see the message:

```bash
Up and running!
```

This confirms that the application successfully started and connected to the running Postgres database.

---

## Development Workflow

- Edit your source code as usual in VS Code.
- Restart the SpringBoot app by stopping and rerunning `./mvnw spring-boot:run` in the terminal.
- Database data persists in the Docker container and will be available across restarts unless explicitly deleted.

---

## Troubleshooting

- Ensure Docker Desktop is running and has enough resources.
- If port 8080 is already in use, stop the conflicting process or adjust port mappings in `docker-compose.yaml` and the SpringBoot application configuration.
- Check PostgreSQL container logs in a separate terminal:

```bash
docker compose logs postgres
```

- Check SpringBoot app logs in the devcontainer terminal for connection issues.

---

## Useful Commands

| Purpose                  | Command                                                     |
|--------------------------|-------------------------------------------------------------|
| Rebuild devcontainer      | `CMD+SHIFT+P` → **Remote-Containers: Rebuild Container**    |
| Check running containers  | `docker ps`                                                 |
| View postgres logs        | `docker compose logs postgres`                              |
| Start SpringBoot app      | `./mvnw spring-boot:run`                                   |
| Stop SpringBoot app       | `CTRL+C` in the terminal window                              |

---

## Additional Resources

- [VS Code Dev Containers Documentation](https://containers.dev/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)
- [Spring Boot Reference Guide](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/)
- [PostgreSQL Docker Image Docs](https://hub.docker.com/_/postgres)
