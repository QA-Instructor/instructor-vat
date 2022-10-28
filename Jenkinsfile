pipeline {
    environment {
        imageName = "vat-calculator:${env.BUILD_ID}"
        dockerImage = ""
    }
    agent any

    stages {
        stage ('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build(imageName)
                }
            }
        }
        stage ('Run calculator') {
            steps {
                script {
                    docker kill vat-calc
                    docker run --name vat-calc -p 3005:80 -d dockerImage
                }
            }
        }

    }
}