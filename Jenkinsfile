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
    }
}