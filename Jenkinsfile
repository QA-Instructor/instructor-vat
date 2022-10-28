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
        stage ('Run app') {
            steps {
                sh "docker kill vat-calc || true"
                sh "docker run --name vat-calc -d -p 3005:80 ${imageName}"
            }
        }
    }
}