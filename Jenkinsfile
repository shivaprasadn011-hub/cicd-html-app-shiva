pipeline {
    agent any

    environment {
        DEPLOY_DIR = "/var/www/html"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/shivaprasadn011-hub/cicd-html-app-shiva.git'
            }
        }

        stage('Build') {
            steps {
                echo "Static HTML project – no build required"
            }
        }

        stage('Package') {
            steps {
                sh '''
                tar -czf weather-app.tar.gz *
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                sudo rm -rf ${DEPLOY_DIR}/*
                sudo tar -xzf weather-app.tar.gz -C ${DEPLOY_DIR}
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Deployment successful. Application is live."
        }
        failure {
            echo "❌ Pipeline failed. Check logs."
        }
    }
}

