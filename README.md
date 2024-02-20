# Python Flask RESTful API

This repository contains a simple Python Flask RESTful API application, which is containerized using Docker. The project is set up with Jenkins for continuous integration and deployment (CI/CD).

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

Before you begin, ensure you have the following tools installed on your system:

- [Python](https://www.python.org/downloads/) (version 3.9 or later)
- [Docker](https://docs.docker.com/get-docker/)
- [Jenkins](https://www.jenkins.io/doc/book/installing/) with Docker Pipeline plugin

### Installing

A step-by-step series of examples that tell you how to get a development environment running.

1. Clone the repository to your local machine:

   ```bash
   git clone https://github.com/yourusername/your-flask-rest-api-repo.git
   cd your-flask-rest-api-repo
   ```

2. Build the Docker image:

   ```bash
   docker build -t yourdockerhubusername/flask-rest-api .
   ```

3. Run the Docker container:
   ```bash
   docker run -d -p 5000:5000 yourdockerhubusername/flask-rest-api
   ```

Now, your application should be running and accessible at `http://localhost:5000`.

## Running the tests

Explain how to run the automated tests for this system (if applicable).

## Deployment

This project is set up with Jenkins for CI/CD. To deploy this application using Jenkins:

1. Set up a new Jenkins pipeline job.
2. Use the `Jenkinsfile` provided in this repository for the pipeline configuration.
3. Run the pipeline job to automatically build, test, and deploy your application.

## Built With

- [Flask](https://flask.palletsprojects.com/) - The web framework used
- [Docker](https://www.docker.com/) - Containerization
- [Jenkins](https://www.jenkins.io/) - Automation server for CI/CD

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
