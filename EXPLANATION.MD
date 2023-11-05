Choice of the base image:
The base image chosen in this Dockerfile is node:alpine3.18. This means that the Docker image will be built on top of the Alpine Linux distribution and will include Node.js as the runtime environment. Alpine Linux is known for its small image size, making it a popular choice for minimizing the image size and improving container startup time.
Dockerfile directives used in the creation and running of each container:

The provided Dockerfile is based on the Node.js Alpine image and sets up a simple Node.js application. Here's a breakdown of each directive:

1. `FROM node:alpine3.18`: Specifies the base image as Node.js Alpine version 3.18.

2. `RUN mkdir -p /envr/myapp/server`: Creates a directory at `/envr/myapp/server` within the container.

3. `WORKDIR /envr/myapp/server`: Sets the working directory to `/envr/myapp/server` for subsequent commands.

4. `COPY package*.json envr/myapp/server`: Copies the `package.json` and `package-lock.json` (if it exists) from the host to the working directory in the container.

5. `RUN npm install --silent`: Installs the Node.js application dependencies specified in `package.json`.

6. `COPY . envr/myapp/server`: Copies the rest of the application files from the host to the working directory in the container.

7. `CMD ["npm", "start"]`: Specifies the default command to run when the container starts. It runs the `npm start` command to start the Node.js application.

This Dockerfile is suitable for creating a Docker container for a Node.js application using the Node.js Alpine base image.


The provided Docker Compose file (`docker-compose.yml`) defines two services, a backend and a client, along with a bridge network named "yolo-network." Additionally, it defines volume mappings for both services. Below is a breakdown of the Docker Compose file:

1. **Version and Services**:
   - `version: "3.7"`: Specifies the Docker Compose file version.

2. **Backend Service**:
   - `build: ./backend`: Specifies the build context for the backend service.
   - `expose: - 5000`: Exposes port 5000 within the container.
   - `ports: - "5000:5000"`: Maps port 5000 on the host to port 5000 on the container.
   - `volumes: - ./backend/src:/envr/myapp/server/src`: Maps the `./backend/src` directory from the host to `/envr/myapp/server/src` within the container.
   - `command: npm run start`: Specifies the command to run when the container starts.
   - `networks: - yolo-network`: Specifies the network to connect the backend service to.

3. **Client Service**:
   - `build: ./client`: Specifies the build context for the client service.
   - `expose: - 3000`: Exposes port 3000 within the container.
   - `ports: - "4000:3000"`: Maps port 4000 on the host to port 3000 on the container.
   - `volumes: 
     - ./client/src:/envr/myapp/client/src
     - ./client/public:/envr/myapp/client/public`: Maps the specified directories from the host to the corresponding directories within the container.
   - `command: npm run start`: Specifies the command to run when the container starts.
   - `networks: - yolo-network`: Specifies the network to connect the client service to.

4. **Network**:
- `networks: yolo-network`: Defines a bridge network named "yolo-network" using the bridge driver.

This Docker Compose configuration sets up a bridge network named "yolo-network" to allow communication between the backend and client services, and it defines volume mappings for persistent data. The exposed ports on the containers are mapped to different ports on the host to allow external access.

Git workflow used to achieve the task. Fork a Git Repository: Start by forking a Git repository on a hosting platform like GitHub, GitLab, or Bitbucket. Initialize a Git repository for your project locally if you haven't already.
Clone the Repository: Clone the repository to my local development environment using the git clone command. Develop and Push: Developed and Pushed my work to the remote repository.
My application run successfully and add two items to the inventory. Image added to root. 

Image of docket hub image record also added.
