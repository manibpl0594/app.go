         properties{
                parameters {
              choice choices: ['service1', 'service2'], description: '', name: 'Select Service'
          }
      }       
      when {
          environment name: 'Select Service', value: 'service1'
      }
      steps{
          sh '''
          cd /service1
          '''
      }
node {
      checkout scm

    docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub_id') {

        def customImage = docker.build("manibpl0509/golang-app:${env.BUILD_ID}")

        /* Push the container to the custom Registry */
        customImage.push()
    }
    }
}
