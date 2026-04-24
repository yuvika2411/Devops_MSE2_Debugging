# DevOps Exam — Test Cases
### KIET Group of Institutions | Even Sem 2026


## Test Case 2 — File Permission Configuration

**Scenario:** A web server requires a properly configured `index.html` file with specific ownership and access permissions.

### Tasks

1. Navigate to your home directory and create a file named `index.html`.
2. Add any HTML text content to the file.
3. Check the file's current default permissions.
4. Grant full permissions (read, write, execute) to all users on the file.
5. Change the file owner and group to `www-data`.
6. Change the file permissions to `755`.
7. Display the final permissions and ownership to verify the configuration.

### Expected Outcome

- File `index.html` exists in the home directory with content.
- After step 4, permissions show `rwxrwxrwx`.
- After step 5, owner and group both show `www-data`.
- Final `ls -l` output shows:
  ```
  -rwxr-xr-x 1 www-data www-data ... index.html
  ```

---

## Test Case 3 — Node.js Application Setup & Git Integration

**Scenario:** You are setting up a new Node.js REST API from scratch and publishing it to GitHub.

### Tasks

1. Initialize a new Node.js project and install the required dependencies: `express` and `@types/express` (as a dev dependency).
2. Create an `index.js` file that starts an Express server on port `8080` with the following endpoint:
   - `GET /health` — returns HTTP status `200` with the JSON response `{ "status": "OK" }`.
3. Initialize a Git repository in the project folder.
4. Create an initial commit with all project files.
5. Create a GitHub repository named `nodejs-api` and push your code to it.

### Expected Outcome

- Project folder contains `package.json`, `node_modules/`, and `index.js`.
- Running the server locally and calling `GET /health` returns:
  ```json
  { "status": "OK" }
  ```
- GitHub repository `nodejs-api` is publicly visible with at least one commit containing all project files.

---

## Test Case 4 — Docker & Containerization

**Scenario:** The Node.js API from Test Case 3 must be packaged into a Docker container for consistent deployment.

### Tasks

1. Write a `Dockerfile` in the project root that:
   - Uses `node:18-alpine` as the base image.
   - Sets `/app` as the working directory.
   - Copies and installs dependencies.
   - Exposes port `8080`.
   - Starts the application using `node index.js`.
2. Build a Docker image named `nodejs-api`.
3. Run the container and verify the `/health` endpoint responds correctly on `http://localhost:8080/health`.
4. Write a `docker-compose.yml` file to run the application as a background service on the same port.

### Expected Outcome

- `docker build` completes with no errors and the image appears in `docker images`.
- The container starts successfully and `GET http://localhost:8080/health` returns:
  ```json
  { "status": "OK" }
  ```
- `docker compose up -d` starts the service in detached mode with no errors.

---
