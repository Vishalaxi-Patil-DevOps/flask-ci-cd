pipeline {
    agent any

    triggers {
        pollSCM('H/1 * * * *') 
     }
    
    environment {
        IMAGE_NAME = "flask-ci-cd"
        IMAGE_TAG = "${BUILD_NUMBER}"
        DOCKER_IMAGE = "${IMAGE_NAME}:${IMAGE_TAG}"
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
                     docker.build("${IMAGE_NAME}:${IMAGE_TAG}", ".")
                    }
                 }
              }
         
         stage('Run Container') {
            steps {
               sh "docker stop ${IMAGE_NAME} || true"
               sh "docker rm ${IMAGE_NAME} || true"
               sh "docker run -d -p 5000:5000 --name ${IMAGE_NAME} ${DOCKER_IMAGE}"
}
}
}
post {
success {
echo 'Deployment'
}
failure {
echo'Deployment failed'
}
}
}


