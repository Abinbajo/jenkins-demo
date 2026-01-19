pipeline {
    agent any

    stages {

        stage('Setup Virtual Environment') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                pip install flask pytest
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

        stage('Deploy') {
            steps {
                sh '''
                echo "Deploying Flask app..."
                rm -rf /opt/simple-app/*
                cp -r . /opt/simple-app/
                '''
            }
        }

        stage('Start Flask App') {
            steps {
                sh '''
                cd /opt/simple-app
                . venv/bin/activate
                nohup python app.py > app.log 2>&1 &
                '''
            }
        }
    }
}

