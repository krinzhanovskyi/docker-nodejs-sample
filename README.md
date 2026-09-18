# To-Do-App with Node.js, Express und Docker

This project is a small web application for managing to-do tasks. The app runs with Node.js and Express and uses either SQLite as database. The application can be run locally or launched in a Docker container.

## Overview

-   Backend: Node.js + Express
-   Frontend: simple HTML/JavaScript interface in the `src/static` folder
-   Database: SQLite by default, PostgreSQL optional
-   Tests: Jest
-   Containerisation: Docker Windows

## Prerequisites

Before you start the project, make sure the following tools are installed on your computer:

-   Git
-   Node.js
-   npm
-   Docker Desktop

Check the installation with:

```bash
git --version
node --version
npm --version
docker --version
```

## Clon repository

```bash
git clone <your-github-repository-url>
cd docker-nodejs-sample
```

## Installing dependencies

Run the following in the project folder:

```bash
npm install
```

This will install all the packages defined in `package.json`, including:

-   `express`
-   `sqlite3`
-   `pg`
-   `uuid`
-   `jest`
-   `nodemon`

```bash
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

## Launching the application on locall server

The launch command is defined in the project:

```bash
npm start
```

The application can then usually be accessed at the following address:

```text
http://localhost:3000
```

## Running tests

```bash
npm test -- runInBand
```

## Database PoSQL and SQL

The project automatically detects whether PostgreSQL is configured:

-   If the environment variable `POSTGRES_HOST` is set, PostgreSQL is used.
-   Otherwise, SQLite is used.
-   You can work as you want.

## Using Docker

For the app to run in a container, a Dockerfile must be present in the project directory. The application can then be built and started using the following commands:

### Build the image

```bash
docker build -t docker-nodejs-sample .
```

### Start the container

```bash
docker run -d -p 3000:3000 --name todo-app docker-nodejs-sample
```

The application is then available again at:

```text
http://localhost:3000
```

### Stop the container

```bash
docker stop todo-app
```

### Remove the container

```bash
docker rm todo-app
```

## Project structure

```text
docker-nodejs-sample/
├── node_modules/
├── spec/
│   ├── persistence/
│   │   └── sqlite.spec.js
│   └── routes/
│       ├── addItem.spec.js
│       ├── deleteItem.spec.js
│       ├── getItems.spec.js
│       └── updateItem.spec.js
├── src/
│   ├── persistence/
│   │   ├── index.js
│   │   ├── postgres.js
│   │   └── sqlite.js
│   ├── routes/
│   │   ├── addItem.js
│   │   ├── deleteItem.js
│   │   ├── getItems.js
│   │   └── updateItem.js
│   ├── static/
│   └── index.js
├── .gitignore
├── package-lock.json
├── package.json
└── README.md
```

## API endpoints

The application provides the following HTTP endpoints:

-   `GET /items` – retrieve all entries
-   `POST /items` – create a new entry
-   `PUT /items/:id` – update an entry
-   `DELETE /items/:id` – delete an entry

## Git workflow

It is advisable to follow a sensible workflow when working on the project:

```bash
git status
git add .
git commit -m ‘FULLY Description of your change’
git push origin main
```

If you are working with a fork, you should push to your own repository.

## Common problems

### 1. "npm" or "node" cannot be found

If the console reports that "npm" cannot be found, Node.js is either not installed or is not available in the PATH. Check again as follows:

```bash
node -v
npm -v
```

### 2. App does not start on port 3000

Check whether another service is already using port 3000. If necessary, change the port in the src/index.js on another one.

### 3. Docker is not running

Make sure that you have WSL and the Docker Desktop is active.

## Licence

This project is licensed under the MIT Licence. The full licence details can be found in `package.json`.

## End

This project serves as a good example of a complete full-stack application using Node.js, Express, database abstraction and Docker containerisation. Thanks to the combination of local development, Git and container setup, it is also well suited as a learning project for application development. Thanks for using.
