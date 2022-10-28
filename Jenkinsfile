pipeline {
    environment {
        imageName = "vat-calculator"
        dockerImage = ""
    }
    agent any

    stages {
        stage ('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build(imageName:${env.BUILD_ID})
                }
            }
        }
    }
}