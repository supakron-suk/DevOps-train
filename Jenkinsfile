pipeline {
    agent any

    stages {
        stage('Clone Source') {
            steps {
                git 'https://github.com/your-username/simple-web.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("simple-web:${BUILD_NUMBER}")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    docker.image("simple-web:${BUILD_NUMBER}").run("-d -p 8081:80")
                }
            }
        }
    }
}
