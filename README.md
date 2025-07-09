# Cloud Development Demo - GitHub Codespaces Setup

This branch demonstrates how to develop and run the **Cloud development demo** SpringBoot application connected to PostgreSQL using **GitHub Codespaces**.

---

## Prerequisites

- A GitHub account with access to Codespaces (your repository should be on GitHub)
- Codespaces enabled for your account / organization

---

## Setup and Run

### 1. Open the repository in GitHub Codespaces

- Navigate to the repository page: [https://github.com/lvoss/cloud-development-demo](https://github.com/lvoss/cloud-development-demo)
- Switch to branch `env-devcontainers`
- Click the green **Code** button and select **Open with Codespaces** → **New codespace**

GitHub Codespaces will build the development container environment based on the included `devcontainer.json`. During this setup, a PostgreSQL database container is automatically started using Docker Compose as configured.

### 2. Start the SpringBoot application

Once the codespace is ready and you have the terminal:

```bash
./mvnw spring-boot:run
```

This starts the SpringBoot application on port 8080.

### 3. Verify the application

Use the **Forwarded Ports** tab in the Codespaces interface to forward port `8080` or open the forwarded port link provided. Open the URL in your browser:

```bash
http://localhost:8080/
```

You should see:

```bash
Up and running!
```

---

## Development Workflow

- Edit your source code directly in the Codespaces editor.
- Restart the SpringBoot app any time by stopping (`CTRL+C`) and restarting `./mvnw spring-boot:run`.
- Postsgres is managed automatically in the container environment.

---

## Troubleshooting

- If the database is not reachable, check containers status with `docker ps` inside the codespace terminal.
- If port forwarding does not work correctly, verify ports are forwarded using the "Ports" panel in Codespaces.
- Check logs for Postgres container with:

```bash
docker compose logs postgres
```

- Monitor SpringBoot app logs in your terminal session.

---

## Useful Commands

| Purpose                  | Command / Notes                                        |
|--------------------------|-------------------------------------------------------|
| Rebuild Codespace         | Use Codespaces interface or `.devcontainer` commands  |
| View running containers   | `docker ps` inside codespace terminal                  |
| View Postgres logs        | `docker compose logs postgres`                         |
| Start SpringBoot app      | `./mvnw spring-boot:run`                              |
| Stop SpringBoot app       | `CTRL+C` in terminal                                   |

---

## Additional Resources

- [GitHub Codespaces documentation](https://docs.github.com/en/codespaces)
- [VS Code Remote - Containers extension docs](https://containers.dev/)
- [Spring Boot Reference Guide](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/)
- [PostgreSQL Docker Image Docs](https://hub.docker.com/_/postgres)
