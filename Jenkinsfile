pipeline {
    agent any

    stages {

        stage('Setup Virtual Environment') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                pip install pytest
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                . venv/bin/activate
                pytest
                '''
            }
        }
    }
}

