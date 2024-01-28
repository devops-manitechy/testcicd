pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    // Build Docker image
                    sh 'docker build -t myapp:latest .'
                }
            }
        }
        
        stage('Push') {
            steps {
                script {
                    // Push Docker image to Docker Hub
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        sh "docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD"
                        sh 'docker push myapp:latest'
                    }
                }
            }
        }
    }
} // This is the missing closing curly brace
