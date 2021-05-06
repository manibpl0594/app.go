node {
   properties([parameters([choice(choices: ['service1', 'service2','service3','service4','service5','service6',
   'service7','service8','service9','service10','service11','service12','service13','service14','service15',
   'service16','service17','service18','service19','service20','service21','service22','service23','service24','service25',
   'service26','service27','service28','service29','service30'], description: '', name: 'Choises')])])
    }
    def name = $Choices
    sh ''' cd $name
       checkout scm {
       docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub_id')
         
        def dockerfile = 'Dockerfile .'
        def customImage = docker.build("manibpl0509/trivy-v2:${env.BUILD_ID}", "-f ${dockerfile}")

        /* Push the container to the custom Registry */
        customImage.push()
}
