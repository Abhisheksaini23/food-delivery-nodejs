pipeline {
    agent any

    tools {
 nodejs 'NodeJS-18'

    }

    environment {
        APP_NAME = "food-delivery-nodejs"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Abhisheksaini23/food-delivery-nodejs.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                echo "No build step needed for Node.js"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
                sh '''
                pm2 stop food-app || true
                pm2 start index.js --name food-app
                '''
            }
        }
    }

    post {
        success {
            echo "✅ CI/CD Pipeline Completed Successfully"
        }
        failure {
            echo "❌ Pipeline Failed"
        }
    }
}

