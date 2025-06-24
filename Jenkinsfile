pipeline {
  agent any

  environment {
    IMAGE_NAME = 'my-simple-app'
    CONTAINER_NAME = 'simple-app-container'
  }

  stages {
    stage('Clone Source') {
      steps {
        git url: 'https://github.com/supakron-suk/DevOps-train.git', branch: 'main'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t $IMAGE_NAME .'
      }
    }

    stage('Run Container') {
      steps {
        sh '''
          docker stop $CONTAINER_NAME || true
          docker rm $CONTAINER_NAME || true
          docker run -d -p 8088:80 --name $CONTAINER_NAME $IMAGE_NAME
        '''
      }
    }
  }
}

