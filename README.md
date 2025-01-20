# React / Django Task Manager App

<p align="center" style="display: flex; justify-content: center; align-items: center;">
  <a href="https://react.dev/" rel="noopener noreferrer" target="_blank">
    <img src="https://dac.digital/wp-content/uploads/2023/11/react-logo-optimized.png" height="120" alt="React Logo">
  </a> 
</p>

<table align="center" > 
  <tr>
    <td>
      <a href="https://vite.dev/" rel="noopener noreferrer" target="_blank">
        <img src="https://de.vitejs.dev/logo-with-shadow.png" height="50" alt="Vite Logo">
      </a>
    </td> 
    <td>
      <a href="https://www.docker.com/" rel="noopener noreferrer" target="_blank">
        <img src="https://www.logo.wine/a/logo/Docker_(software)/Docker_(software)-Logo.wine.svg" height="100" alt="Docker Logo">
      </a>
    </td>
    <td>
      <a href="https://tagmanager.google.com/" rel="noopener noreferrer" target="_blank">
        <img src="https://img.icons8.com/color/512/google-tag-manager.png" height="50" alt="GTM Logo">
      </a>
      <a href="https://marketingplatform.google.com/about/analytics/" rel="noopener noreferrer" target="_blank">
        <img src="https://miro.medium.com/v2/resize:fit:1400/1*-ExxDAPl4rciaENKd8QSBw.png" height="60" alt="GA4 Logo">
      </a>
    </td>
  </tr>
</table>

## Description

This repository contains task management platform application (frontend-only).

### Technologies Used

- **Frontend**: Built on React with TypeScript, utilizes a custom Express server with Vite as middleware

### Additinal features include:

- **Frontend Logger** - winston debug & error logger with rotating file handlers;
- **GTM** and **Google Analytics 4** - setup for tracking cookies;
- **Dockerized**: Easy setup and deployment

---

## Prerequisites

Ensure you have the following installed on your machine:

- [Node.js](https://nodejs.org/) (version **22** or higher) (if running locally)
- [npm](https://www.npmjs.com/) (version **10** or higher) (if running locally)
- [Docker](https://www.docker.com/) (latest version)
- [Docker Compose](https://docs.docker.com/compose/) (latest version)

---

## Getting Started

#### 1. Make a folder where you will store the code:

```bash
mkdir react-task-app
```

#### 2. Clone the repository in the folder of your choice:

```bash
git clone https://github.com/konnikamii/react-task-app.git .
```

## Frontend Setup

#### 1. Navigate to the frontend directory:

```bash
cd frontend
```

#### 2. Copy the example environment file and configure it:

```bash
cp .env.example .env
```

#### 3. Make new directories for the named volumes:

```bash
mkdir node_modules
mkdir logs
mkdir dist
mkdir dist-server
```

#### 4. Install Node.js dependencies using npm: (only if running locally)

```bash
npm install
```

#### 5. Start the Vite development server: (only if running locally)

```bash
npm run dev
```

## Docker Setup

#### 1. Navigate to the root directory:

```bash
cd ..
```

#### 2. Build and start the Docker containers:

```bash
docker compose up --build
```

### Access the application:

By default:

- The **frontend** will be available at [http://localhost:3000](http://localhost:3000)

You would need to hook it up to a backend to create an account and log in.

---

### Additional Information:

By default, the copied `.env` file should work out of the box you run `docker compose up`.
However, if any errors occur, ensure the correct **hostnames**, **ports**, and **credentials** are specified.

If you want to start the **production build** run the following command:

```bash
docker compose -f docker-compose-prod.yaml up --build
```

To destroy containers use:

```bash
docker compose -f docker-compose-prod.yaml down
```

---

#### GTM & GA4

If you want to connect your application to google services you need to create **GTM** account and **GA4** account. Then copy each of the unique IDs and replace them in your frontend `.env` file.

#### Helpfull commands for Docker

```bash
docker compose up                                                 # builds images and starts the containers (dafaults to: ./docker-compose.yaml ./.env)
docker compose down                                               # removes containers
docker compose config                                             # troubleshoots the setup

docker compose up --build                                         # forces image rebuilds
docker compose --project-name "my-app" up                         # flag for setting project name (if not specified)
docker compose -p "my-app" up                                     # shorthand for project name
docker compose -f <filename.yaml> up                              # runs a particular 'docker-compose.yaml' file
  
docker ps                                                         # lists all containers
docker logs <container_name_or_id>                                # check logs of container
docker stats                                                      # tracks active container resource utilization

docker exec -it <container_name_or_id> /bin/sh                    # enter container using shell
docker exec -it <container_name_or_id> bash                       # enter container using bash (if installed)
```
