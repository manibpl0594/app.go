pipeline {
  agent any
  environment {
    DOCKER_REPO = "manibpl0504/golang-app"
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
        sh '''
        docker login -u manibpl0509 -p Dust@321D
        '''
      }
    }

    stage ('push image') {
      steps {
        sh '''
        docker push ${DOCKER_REPO}:${BUILD_NUMBER}
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
