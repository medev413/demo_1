pipeline {
    agent any

    stages {
        stage('docker_check') {
             steps {
                echo 'Checking if Docker is installed...'
                sh 'docker --version'
                sh 'which docker'
            }
        }
        stage('Build') {
            steps {
                echo 'Building docker image...'
                sh 'docker build -t my-nginx-image .'
            }
        }
        stage('Run') {
            steps {
                echo 'Running docker container...'
                sh 'docker run -d -p 9080:80 --name my-nginx-container my-nginx-image'
            }
        }
    }
}