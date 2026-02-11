pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                   
                    checkout scm
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    
                    sh 'docker build -t my-image:latest .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    try {
                       
                        sh 'docker run --name my-container my-image:latest'
                    } catch (Exception e) {
                        
                        sh 'docker ps -a'
                        error "Docker container failed: ${e.message}"
                    }
                }
            }
        }
    }

    post {
        always {
            script {
                
                sh 'docker rm -f my-container || true'
                sh 'docker rmi my-image:latest || true'
            }
        }
    }
}