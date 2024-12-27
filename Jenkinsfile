pipeline {
    agent any
    
    environment {
        DEPLOY_SERVER = 'ubuntu@<apache-instance-public-ip>'  // Replace with the Apache server's public IP.
        DEPLOY_DIR = '/var/www/html'  // This is where your Apache serves files from.
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                // Here, if necessary, build your project. For a simple HTML file, you can skip this step.
                echo "Build stage - Skipping build for simple HTML project"
            }
        }

        stage('Deploy') {
            steps {
                // Deploy to Apache server on EC2
                echo "Deploying to Apache server"
                sh '''
                    # Copy the HTML files to the Apache web directory
                    scp -i /path/to/your/private-key.pem -r * ${DEPLOY_SERVER}:${DEPLOY_DIR}
                '''
            }
        }
    }
}
