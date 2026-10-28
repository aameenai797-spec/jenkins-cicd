
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cicd-flask-app:latest .'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'docker run --rm cicd-flask-app:latest python -m pytest -v'
            }
        }
    }

    post {
        success {
            echo 'Build and tests completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the console output.'
        }
    }
}
