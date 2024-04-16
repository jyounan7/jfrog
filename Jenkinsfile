pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Checkout the source code from your repository
                git 'https://github.com/jyounan7/jfrog.git'

                // Build the Docker image
                script {
                    docker.build('test:latest')
                }
            }
        }

        stage('Push to JFrog Artifactory') {
            steps {
                script {
                    // Login to JFrog Artifactory
                    docker.withRegistry('http://192.168.1.10:8082/artifactory/frontend/', 'jcr') {
                        // Push the Docker image to JFrog Artifactory
                        docker.image('your-docker-image-name:latest').push('latest')
                    }
                }
            }
        }
    }
}
