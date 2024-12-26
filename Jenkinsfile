pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Git is automatically pulling from GitHub, so this step isn't needed.
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image from the Dockerfile
                    sh 'docker build -t my-html-site .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run the Docker container on port 8000
                    sh 'docker run -d -p 8000:80 my-html-site'
                }
            }
        }
    }
}
