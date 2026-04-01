pipeline {
    agent any

    environment {
        DOCKER = '"C:\\Program Files\\Docker\\Docker\\resources\\bin\\docker.exe"'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                bat '%DOCKER% build -t python-app .'
            }
        }

        stage('Run Tests Inside Docker') {
            steps {
                bat '%DOCKER% run --rm python-app pytest'
            }
        }

        stage('Run Application') {
            steps {
                bat '%DOCKER% run --rm python-app'
            }
        }
    }
}