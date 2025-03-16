---
icon: bullseye-arrow
---

# Running Project

## Running the Project Locally

### Prerequisites

* **Node.js** and **NPM** installed.
* **PostgreSQL** database setup.
* Environment variables configured in a `.env`file.

### Steps to Run

1.  **Clone the Repository**

    ```bash
    git clone https://github.com/codescnepal13/sparepartsserver
    cd sparepartsserver
    ```
2.  **Install Dependencies**

    ```bash
    npm install
    ```
3.  **Configure Environment Variables.** Create a `.env` file in the root directory and add:\


    ```env
    DATABASE_URL=postgresql://username:password@localhost:5432/your_database_name
    JWT_SECRET=your_jwt_secret
    PORT=8000
    ```
4.  Run Database Migrations

    ```bash
    npx prisma migrate dev
    ```
5.  Start the Development Server

    ```bash
    npm run dev
    ```
6.  Access the Application: After running the server, your application is exposed on port 8000, open a browser and go to:

    ```
    http://localhost:8000
    ```

## Running the Project with Docker

Follow the steps below to run the project using Docker and Docker Compose.

### Prerequisites

Make sure you have the following installed on your system:

* Docker
* Docker Compose

### Steps to Run

1.  **Clone the Project**

    ```bash
    git clone https://github.com/codescnepal13/sparepartsserver
    cd sparepartsserver
    ```
2.  Build and Run the Project with Docker Compose\
    Docker Compose will automatically build Docker images and start the application as defined in  `docker-compose.yml`&#x20;

    ```bash
    docker-compose build
    docker-compose up
    ```

    By default, Docker Compose runs in the foreground. If you want to run the containers in the background (detached mode), use the `-d` flag:

    ```bash
    docker-compose up -d
    ```

    Docker Compose will pull any required images, build our custom images, and start the containers.
3.  Verify the Running Containers\
    Once the containers are up, verify they are running using:

    ```bash
    docker ps
    ```
4.  Access the Application: After running the server, your application is exposed on port 8000, open a browser and go to:

    ```
    http://localhost:8000
    ```
5.  Stopping the Containers\
    To stop the running containers, execute the following command:

    ```bash
    docker-compose down

    ```

## Testing the API

Use a tool like Postman or Insomnia to test the API endpoints locally.

