Full-Stack Application with React, Django, and PostgreSQL
This repository contains a full-stack application with the following services:

Frontend: React application

Backend: Django application with PostgreSQL integration

Database: PostgreSQL database

Docker and Docker Compose are used to easily build, run, and manage all services.

Prerequisites
Before using this setup, make sure you have the following installed on your machine:

Docker

Docker Compose

Project Structure
bash
Copy
/my_project
│
├── /bank-front-master  # React front-end code
├── /bank-master        # Django back-end code
└── docker-compose.yml  # Docker Compose file for managing services
bank-front-master/: Contains the React application files.

bank-master/: Contains the Django application files.

docker-compose.yml: Defines the services (Frontend, Backend, PostgreSQL).

Docker Compose Commands
1. Build Docker Images
   To build the Docker images for the front-end, back-end, and PostgreSQL, run:

bash
Copy
docker-compose build
This command will:

Build the React app Docker image using the Dockerfile in the bank-front-master directory.

Build the Django app Docker image using the Dockerfile in the bank-master directory.

Pull the postgres:13 image to set up the PostgreSQL database service.

2. Start the Application
   Once the images are built, start the application using:

bash
Copy
docker-compose up
This will:

Start the PostgreSQL database service on port 5432.

Run the Django backend service on port 8000, automatically applying database migrations (python manage.py migrate).

Launch the React frontend service on port 3000, starting the React development server (npm run start).

3. Stop and Remove Containers
   To stop and remove the running containers, use:

bash
Copy
docker-compose down
This command will:

Stop all running containers.

Remove the containers, networks, and volumes created by docker-compose up.

4. Viewing Logs
   To view the logs of all services running in the Docker Compose setup, use:

bash
Copy
docker-compose logs
To view logs for a specific service, like the backend or frontend, specify the service name:

bash
Copy
docker-compose logs backend
bash
Copy
docker-compose logs frontend
Accessing the Application
After running docker-compose up, you can access the following:

Frontend (React): Visit http://localhost:3000 to view the React application.

Backend (Django): Visit http://localhost:8000 to access the Django application (or use it as an API endpoint).

PostgreSQL Database: The PostgreSQL database will be available on localhost:5432, but typically, you interact with it through Django.

Volumes and Persistence
The PostgreSQL data is stored in a Docker volume (postgres_data), ensuring that your data persists even after containers are stopped or removed.

Troubleshooting
If you're having issues with the services not starting, here are a few things to check:

Ensure you've built the images by running docker-compose build before running docker-compose up.

Ensure that PostgreSQL is running and accessible for Django.

Double-check the database connection URL in the Django settings.

Additional Notes
If you want to manually create and apply Django database migrations, you can access the backend container and run:

bash
Copy
docker-compose exec backend bash
python manage.py migrate
This will allow you to run Django commands inside the backend container.

License
This project is licensed under the MIT License – see the LICENSE file for details.