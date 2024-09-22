# Docker-Dev-Template

This repo has a mock-up of a docker build for hello world python web app.

## Key Components

**Dockerfile**: This file defines the build of our container. It takes a base python image, sets up teh file structure, installs the packages, and calls the app to run.

**requirements.txt**: A list of python packages used in the build.

**src/main.py**: The folder with our python scripts. The main.py script initialises a FastAPI instance, handles a get request at the path root, and prints a json statement.

## Running the App

1. Build the container: 

```
docker build -t docker-dev-template .
```

2. Run the Docker container:

```
docker run -d -p 8000:8000 docker-dev-template
```

3. Check the app is running at http://127.0.0.1:8000/

4. Register file changes with Docker Volumes:

    - Identify the name of the running container. Then stop the container running. Then re-run it with an additional command to mount the local cwd on the host machine.

```
docker ps
docker stop CONTAINER [container_name]
docker run -d -p 8000:8000 -v "$(pwd):/code" docker-dev-template
```

5. Use an IDE in the Docker container:

    - In VSCode, download the Docker and Dev Containers extensions.
    - Search for the command "Dev Containers: Attach to running container..."
    - Select the running container
    - This will launch a new vscode instance running inside the container
