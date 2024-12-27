pipeline {
    agent any
    environment {
        DEPLOY_SERVER = 'ubuntu@13.60.188.164'  // Apache server EC2 IP
        REMOTE_DIR = '/var/www/html'  // Default Apache directory
    }
    stages {
        stage('Clone Repository') {
            steps {
                // Checkout the repository from GitHub
                git 'https://github.com/sarmadhamdani02/tocs_project'
            }
        }
        stage('Deploy to Apache Server') {
            steps {
                script {
                    // Use the Jenkins credentials for the private key
                    withCredentials([file(credentialsId: 'apache-ssh-key', variable: 'PRIVATE_KEY_PATH')]) {
                        // Copy the index.html to the Apache server
                        sh """
                        scp -i ${PRIVATE_KEY_PATH} -o StrictHostKeyChecking=no index.html ${DEPLOY_SERVER}:${REMOTE_DIR}/
                        """
                    }
                }
            }
        }
    }
}
