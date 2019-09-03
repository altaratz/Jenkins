pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/kinecosystem/kre-compute-engine.git#dev'
            }
        }
        stage('Build image') {
            steps {
                ### This build the actual image ###
                echo 'Docker build'
                sh 'docker build -t krejenkins/test:${BUILD_NUMBER} .'
            }
        }
        stage('Push Docker image') {
            steps {
                echo 'Pushing to DockerHub'
                sh 'docker push krejenkins/test:${BUILD_NUMBER}'
            }
        }
    }
}
