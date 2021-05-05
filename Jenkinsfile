properties([parameters([choice(choices: ['service1', 'service2'], description: '', name: 'Choises')])])
node {
   if (Choises.equals("service1")){
    checkout scm
    docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub_id') {
        def dockerfile = '/var/lib/jenkins/workspace/docker/service1/Dockerfile .'
        def customImage = docker.build("manibpl0509/trivy-v2:${env.BUILD_ID}", "-f ${dockerfile}")

        /* Push the container to the custom Registry */
        customImage.push()
    }
   }
   else if (Choises.equals("service2")){
    checkout scm
    docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub_id') {
        def dockerfile = '/var/lib/jenkins/workspace/docker/service2/Dockerfile .'
        def customImage = docker.build("manibpl0509/golang-app:${env.BUILD_ID}", "-f ${dockerfile}")

        /* Push the container to the custom Registry */
        customImage.push()
   }
}
}
