pipeline {
    agent any
    environment {
        DEPLOY_SERVER = 'ubuntu@13.60.188.164'  // Apache server EC2 IP
        PRIVATE_KEY = '/path/to/your/private-key.pem'  // Path to your private key on Jenkins instance
        REMOTE_DIR = '/var/www/html'  // Default Apache directory
    }
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/yourusername/yourrepo.git'
            }
        }
        stage('Deploy to Apache Server') {
            steps {
                script {
                    // Copy the index.html to the Apache server
                    sh """
                    scp -i ${PRIVATE_KEY} index.html ${DEPLOY_SERVER}:${REMOTE_DIR}/
                    """
                }
            }
        }
    }
}
