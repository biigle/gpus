# BIIGLE GPU Server

Application to process jobs submitted from BIIGLE on a GPU.

## Requirements

- [Docker](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Available Python Packages

All GPU modules should use Python 3 for computation, so run all scripts with `python3`. See the [`requirements.txt`](.docker/requirements.txt) for the available Python 3 packages.

## Installation

### For Production

Run `docker-compose build` to build the `biigle/gpu-server`, `biigle/gpu-server-web` and `biigle/gpu-server-worker` Docker images.

Now head over to [the distribution repository (TODO)](#) to configure and build your production setup.

### For Development

To develop the BIIGLE GPU server on your local machine you may use Docker containers, too. This way you don't need to install any of the requirements like Python or special PHP extensions and keep your development environment clearly separated from your regular OS.

#### Download the project files

Set up the project in the `biigle-gpu-server` directory (using [Composer](https://getcomposer.org/doc/00-intro.md)):

```
composer create-project biigle/gpu-server:dev-master --repository='{"type":"vcs","url":"git@github.com:biigle/gpu-server.git"}' --keep-vcs --ignore-platform-reqs --prefer-source biigle-gpu-server
```

Note the `--ignore-platform-reqs` flag to keep Composer from complaining about missing requirements. These requirements will be met by the Docker containers.

#### Build and run the application

Now you have to configure `GITHUB_OAUTH_TOKEN` in the `.env` file with a [personal access token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/) of GitHub (with authorization for the **repo** scope).

This allows you to build the Docker images and start the application with `docker-compose up`. The first time may take a while. The BIIGLE GPU server application is now running at `http://localhost:8001`. Stop the containers with `docker-compose stop`. Destroy them (and the development database) with `docker-compose down`.
