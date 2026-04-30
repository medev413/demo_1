pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                checkout scm: [
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: 'https://github.com/medev413/demo_1.git']]
                ]
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