# Pigeon CLI

## Introduction

This repository contains a collection of custom commands to simplify development workflows, including Docker management, Git operations, and Laravel Sail interactions. It streamlines common tasks, helping developers automate and speed up their processes.

## Requirements

- Composer 2.0 or later

To easily run Composer-installed executables from your terminal, add the Composer vendor bin directory to your shell's `PATH`. This avoids having to specify the full path each time.

1.  Open your shell configuration file in a text editor (e.g. `nano ~/.bashrc`).

2.  Add the following line to the file:

    ```bash
    export PATH="$PATH:$HOME/.config/composer/vendor/bin"
    ```

3.  Save the file.

4.  Apply the changes to your current shell session by sourcing the configuration file:

    ```bash
    source ~/.bashrc
    ```

## Installation

```bash
composer global require pigeonboys/pigeon-cli
```

## Commands

| Command        | Arguments | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| -------------- | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| fucking-docker | -f        | Forcefully stops all running Docker containers and then performs system cleanup. If the `-f` flag is passed as an argument, it removes all unused images, containers, and networks. Regardless, it prunes unused volumes and deletes the Docker configuration file.                                                                                                                                                                                                                                                                                             |
| dock           |           | Loads environment variables from a `.env` file in the current directory, then starts an interactive Bash session inside a running Docker container whose name matches the `$PROJECT_NAME` variable and begins with "web".                                                                                                                                                                                                                                                                                                                                       |
| d              |           | Checks for the existence of a `.env` file and loads the `PROJECT_NAME` environment variable from it. It then runs a command inside a Docker container matching the `$PROJECT_NAME` variable and starting with "`web.`" If the first argument (`$1`) is not one of `bash`, `composer`, `npm`, `pest`, or `pint`, it defaults to running a Laravel Artisan command (`php artisan`). If the argument matches one of those excluded commands, it simply runs the specified command inside the container. If the `.env` file is missing, it prints an error message. |
| sail           |           | Forwards all arguments (`$@`) to the `vendor/bin/sail` command, which is part of Laravel Sail (a command-line interface for interacting with Docker containers in Laravel projects). It allows users to run any Sail command specified as an argument to the script.                                                                                                                                                                                                                                                                                            |
| s              |           | Checks if the first argument (`$1`) is not one of `bash`, `composer`, `npm`, `pest`, or `pint`. If it's a different command, it forwards the arguments to `vendor/bin/sail artisan` to run a Laravel Artisan command inside the Sail environment. If the argument is one of the excluded commands, it directly forwards the arguments to `vendor/bin/sail` to execute the corresponding Sail command.                                                                                                                                                           |
| up2date        |           | This script updates system packages, removes unnecessary ones, and globally updates Composer dependencies with a single command.                                                                                                                                                                                                                                                                                                                                                                                                                                |
| git-amnesia    |           | Creates an initial commit in the Git repository by resetting the current `HEAD` to the tree of the first commit. It uses the git commit-tree command to create a new commit with the message "`Initial commit.`" and resets the working directory to that commit. This effectively resets the repository to an initial state while keeping the commit history intact.                                                                                                                                                                                           |
