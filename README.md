# Project 8: Build and Run Docker App Locally

## Objective

Practice building a Docker image, running a container, and verifying a web application locally.

## Project summary

This project was completed on an Ubuntu VM. The Flask application serves a confirmation page at `/` and listens on port `5000` inside the container. The Dockerfile uses `python:3.11-slim` and installs Flask and its dependencies from the files in `packages/` using `pip --no-index`. The base image must already be cached or available to pull.

**Technologies:** Ubuntu, Docker, Python 3.11, and Flask.

## Ubuntu project layout

```text
P8-Docker-Local-App/
  app.py
  Dockerfile
  requirements.txt
  packages/
  README.md
  screenshots/
```

The source files and dependency packages are on the Ubuntu VM. This copy contains the project summary and a folder for the screenshots.

## Build, run, and verify

Run these commands from the original project directory on the Ubuntu VM. If `my-flask-container` is already running, skip `docker run` and use the verification commands.

```bash
cd ~/P8-Docker-Local-App
ls -la
docker build --no-cache -t my-docker-app .
docker images my-docker-app
docker run -d -p 5000:5000 --name my-flask-container my-docker-app
docker ps --filter name=my-flask-container
curl -fsS http://localhost:5000/
```

Open [http://localhost:5000](http://localhost:5000) in a browser **inside the VM**. Confirm that the page shows **Docker App Running Successfully!**, followed by “My first Dockerized Python application.” and “Project 8 - Container Deployment”.

## Screenshots

Save these files in `screenshots/`. Capture the container and browser evidence before stopping the container.

| Filename | What to capture |
| --- | --- |
| `1-docker-image.png` | `docker images my-docker-app` showing the tagged image |
| `2-container-running.png` | `docker ps` showing `my-flask-container` is `Up` and host port `5000` maps to container port `5000` |
| `3-browser-output.png` | The Flask confirmation page with `http://localhost:5000` visible in the address bar |
| `4-docker-build.png` | The successful build output showing the image was tagged as `my-docker-app` |

<!--
### 1. Docker image
![Tagged Docker image](./screenshots/1-docker-image.png)

### 2. Running container
![Running Flask container](./screenshots/2-container-running.png)

### 3. Application output
![Flask confirmation page](./screenshots/3-browser-output.png)

### 4. Docker build
![Successful Docker build](./screenshots/4-docker-build.png)
-->

After adding the four images, remove the `<!--` and `-->` lines around the image section above so GitHub displays them.

## GitHub submission

Copy this README and the screenshots into the original Ubuntu project. Review the files for credentials or private information before committing. For a new repository, create an empty GitHub repository named `P8-Docker-Local-App`, replace `YOUR_USERNAME`, and run:

```bash
git init
git add app.py Dockerfile requirements.txt packages/ README.md screenshots/
git commit -m "Complete Project 8 Docker local app"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/P8-Docker-Local-App.git
git push -u origin main
```

If the project already has an `origin`, check `git remote -v` and verify that it points to the intended repository before pushing.

## Submission checklist

- [ ] Docker image screenshot
- [ ] Running container screenshot
- [ ] Browser output screenshot
- [ ] Successful build screenshot
- [ ] README with all screenshots displayed
- [ ] GitHub repository link: _add after pushing_
