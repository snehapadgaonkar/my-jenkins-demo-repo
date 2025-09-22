pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/SamidhaManjrekar/my-jenkins-demo-repo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("myapp:${BUILD_NUMBER}", "app")
                }
            }
        }

        stage('Run App') {
            steps {
                script {
                    sh 'docker rm -f myapp-container || true'
                    sh "docker run -d --name myapp-container -p 8081:80 myapp:${BUILD_NUMBER}"
                }
            }
        }
    }
}
