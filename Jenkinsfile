pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('suyogbc/suyogjenkins:latest', '-f Dockerfile .')
                }
            }
        }
        
        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
                        docker.image('suyogbc/suyogjenkins:latest').push('latest')
                    }
                }
            }
        }
    }
}
