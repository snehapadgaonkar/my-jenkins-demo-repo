pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/snehapadgaonkar/my-jenkins-demo-repo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("myapp:${BUILD_NUMBER}")
                }
            }
        }

        stage('Run App') {
            steps {
                script {
                    sh 'docker run --rm myapp:${BUILD_NUMBER}'
                }
            }
        }
    }
}
