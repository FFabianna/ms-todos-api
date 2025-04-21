# ✅ ms-todos-api

This microservice handles the management of to-do items. It is a Node.js application that runs inside a Docker container and communicates with other services such as Redis and the Auth API.

---

## 🔗 Project Links

- 📋 [Trello Board](https://trello.com/invite/b/680296aa17864e87fc6c7fed/ATTI82505e108ae3e7a005ede0081ec437f87CDDDEF1/microservice)
- 📄 [Project Documentation](https://docs.google.com/document/d/1FER2lpkZJk2eI5tpMnMy8mFhd42g3f4jioasHwZ0klo/edit?usp=sharing)


---

## 🐳 Docker Image

The service uses the Node.js 8.17.0 image as the base. It:

1. Sets up the working directory.
2. Installs dependencies from `package.json`.
3. Exposes port 8082 (default API port).
4. Starts the server using `npm start`.

---

## ☸️ Kubernetes Deployment

- Deploys one replica of the container with the label `app: todosapi`.
- Exposes the container internally using a `ClusterIP` service on port 8082.
- Sets an environment variable for `ZIPKIN_URL` to enable distributed tracing.

---

## 🔁 CI/CD Pipeline

GitHub Actions automate:

1. Checkout and tag based on commit SHA.
2. Login to Azure and ACR (Azure Container Registry).
3. Build and push the Docker image to ACR.
4. Apply Kubernetes deployment and service configuration.
5. Update the deployment image with the newly pushed version.

---

## 📢 Slack Integration

A secondary GitHub Actions workflow notifies a Slack channel when changes are pushed to the `main` branch. This helps keep the team informed of updates in the `ms-todos-api` microservice repository.

---

## 📦 Environment Variables

| Variable         | Description                                 |
|------------------|---------------------------------------------|
| `AUTH_API_ADDRESS` | URL of the authentication service          |
| `TODOS_API_ADDRESS` | Self-reference for internal communication |
| `TODO_API_PORT`   | Port on which the API listens (default: 8082) |
| `JWT_SECRET`      | Secret for JWT verification                |
| `REDIS_HOST`      | Redis service hostname                     |
| `REDIS_PORT`      | Redis service port (default: 6379)         |
| `REDIS_CHANNEL`   | Redis pub/sub channel used for logs        |

---
## <b> Made by </b>

+ [Fabiana Valderruten](https://github.com/FFabianna "FFabianna")
+ [Gloria Vicuña](https://github.com/Vanesa155 "Vanesa V.")

[![forthebadge](https://forthebadge.com/images/badges/built-with-love.svg)](https://forthebadge.com)
