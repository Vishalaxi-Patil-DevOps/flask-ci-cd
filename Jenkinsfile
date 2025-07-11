pipeline {
    agent any 
    
    enviornmnet {
        IMAGE_NAME = "flask-ci-cd"
        DOCKER_IMAGE = "flask-ci-cd-latest"
                 }
    stages {
        stage('Clone') {
             steps {
                 git 'https://github.com/Vishalaxi-Patil-DevOps/flask-ci-cd.git'
           }
         }
        stage('Build Docker Image') {
            steps {
                script {
                     docker.build("${IMAGE_NAME}", ".")
                    }
                 }
              }
         }


