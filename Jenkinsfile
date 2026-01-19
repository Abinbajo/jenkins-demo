pipeline {
  agent any

  stages {
    stage('Build Image') {
      steps {
        sh 'docker build -t simple-flask:latest .'
      }
    }

    stage('Run Container') {
      steps {
        sh '''
          docker rm -f simple-flask || true
          docker run -d \
            --name simple-flask \
            -p 5000:5000 \
            simple-flask:latest
        '''
      }
    }
  }
}

