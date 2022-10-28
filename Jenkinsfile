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
                docker stop vat-calc || true
                docker rm vat-calc || true
                docker run --name vat-calc -d -p 3005:80 ${imageName}
            }
        }
    }
}