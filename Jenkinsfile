pipeline {
  agent any
  environment {
    DOCKER_REPO = "manibpl0509/golang-app"
  }

  stages {
    stage ('Build Image') {
      steps {
        sh '''
        docker build -t ${DOCKER_REPO}:${BUILD_NUMBER} .
        '''
      }
    }
    stage ('Docker login') {
      steps {
       docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub_id')
      }
    }

    stage ('push image') {
      steps {
        sh '''
        docker push ${DOCKER_REPO}:${BUILD_NUMBER}
        '''
        }
    }
    stage ('Cleanup') {
      steps {
        sh '''
        docker rmi ${DOCKER_REPO}:${BUILD_NUMBER} -f
        '''
        }
    }
  }
}
  }
}
