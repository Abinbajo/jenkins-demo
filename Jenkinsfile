pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Abinbajo/jenkins-demo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install pytest'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest'
            }
        }
    }
}
