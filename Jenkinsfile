pipeline {
    agent any

    stages {

        stage("Checkout Repo") {
            steps {
                checkout scm
            }
        }

        stage("Build Docker Image") {
            steps {
                sh 'docker build -t python-docker-jenkins .'
            }
        }

        stage("Stop Old Container") {
            steps {
                sh '''
                docker stop python-docker || true
                docker rm python-docker || true
                '''
            }
        }

        stage("Run Docker Container") {
            steps {
                sh '''
                docker run -d -p 5000:5000 --name python-docker python-docker-jenkins
                '''
            }
        }
    }
}

