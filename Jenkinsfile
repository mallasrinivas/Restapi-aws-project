pipeline {
    agent any
    
    environment {
        // Define environment variables
        IMAGE_NAME = 'mallasrinivas/flask-rest-api'
        IMAGE_TAG = 'latest'
        CONTAINER_NAME = 'flask-app'
        APP_PORT = 5000 // Port the Flask app runs on
    }

    stages {
        stage('Checkout') {
            steps {
                // Replace with your repository URL
                git 'https://github.com/yourusername/your-flask-rest-api-repo.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    // Building Docker image from Dockerfile
                    sh "docker build -t ${env.IMAGE_NAME}:${env.IMAGE_TAG} ."
                    // Pushing Docker image to Docker Hub
                    sh "docker login -u mallasrinivas -p yourdockerhubpassword"
                    sh "docker push ${env.IMAGE_NAME}:${env.IMAGE_TAG}"
                }
            }
        }
        
        stage('Run Docker Container') {
            steps {
                script {
                    // Pulling Docker image from Docker Hub
                    sh "docker pull ${env.IMAGE_NAME}:${env.IMAGE_TAG}"
                    // Stop and remove any previous instance of the Docker container
                    sh "docker stop ${env.CONTAINER_NAME} || true && docker rm ${env.CONTAINER_NAME} || true"
                    // Running Docker container
                    sh "docker run -d -p ${env.APP_PORT}:${env.APP_PORT} --name ${env.CONTAINER_NAME} ${env.IMAGE_NAME}:${env.IMAGE_TAG}"
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    // A simple health check
                    // Adjust the sleep time as necessary based on your application startup time
                    sh 'sleep 5'
                    sh "curl http://localhost:${env.APP_PORT}/"
                }
            }
        }
    }

    post {
        // always {
        //     // Clean up by stopping and removing the container
        //     sh "docker stop ${env.CONTAINER_NAME} || true"
        //     sh "docker rm ${env.CONTAINER_NAME} || true"
        // }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
