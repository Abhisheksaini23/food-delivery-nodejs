
pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Abhisheksaini23/food-delivery-nodejs.git'
            }
        }

        stage('Verify Node & NPM') {
            steps {
                bat 'node -v'
                bat 'npm -v'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                pm2 stop food-app || echo Not running
                pm2 start index.js --name food-app
                '''
            }
        }
    }

    post {
        success {
            echo '✅ CI/CD Pipeline Completed Successfully'
        }
        failure {
            echo '❌ CI/CD Pipeline Failed'
        }
    }
}
