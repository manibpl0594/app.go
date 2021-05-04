node {
    properties([parameters([choice(choices: ['service1', 'service2'], description: '', name: 'Choises')])])
   if (Choises.equals("service1")){
        sh ''' cd /var/lib/jenkins/workspace/docker/service1/ '''
    checkout scm
    docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub_id') {
        def dockerfile = '/var/lib/jenkins/workspace/docker/service1/Dockerfile'
        def customImage = docker.build("manibpl0509/trivy:${env.BUILD_ID}", "-f ${dockerfile} ./dockerfiles")

        /* Push the container to the custom Registry */
        customImage.push()
    }
   }
   else if (Choises.equals("service2")){
    sh ''' cd service2 '''
    checkout scm
    docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub_id') {

        def customImage = docker.build("manibpl0509/golang-app:${env.BUILD_ID}")

        /* Push the container to the custom Registry */
        customImage.push()
   }
}
}
