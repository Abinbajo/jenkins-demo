pipeline {
    agent any

    stages {
        stage('Build Image') {
            steps {
                sh 'docker build -t jenkins-flask-app:1.0 .'
            }
        }

        stage('Load Image into Kind') {
            steps {
                sh 'kind load docker-image jenkins-flask-app:1.0'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                kubectl apply -f deployment.yaml
                kubectl apply -f service.yaml
                '''
            }
        }
    }
}

