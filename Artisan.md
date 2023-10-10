# Artisan in laravel

## Introduction
Artisan is a command line interface embeded with Laravel. It is root for the application as the scripts and commands are utilites for easy workflow. 

### Laravel Sail
Laravel sail is a lightweight command-line interface for interacting with laravel's default Docker development environment. It is helpful for building Laravel application using PHP, MySQL, and Redis without prior Docker experience.
It also provides convenient methods for interacting with the Docker containers defined by the docker-compose.yml file. When using Laravel Sail, your application is executing within a Docker container and is isolated from your local computer.

## Writing Commands
Commands are typically stored in `app/Console/Commands` directory.
-creating new commands
to create new commands we use `make:command` Artisan command. This will create a new command class in the `app/Console/Commands` directory.