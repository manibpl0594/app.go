    CHOICES = [];
    pipeline{
       agent { label 'master'} 
       stages {
          stage ("build") {
            steps {
                script {
                 CHOICES = ['service1', 'service2','service3','service4','service5','service6',
   'service7','service8','service9','service10','service11','service12','service13','service14','service15',
   'service16','service17','service18','service19','service20','service21','service22','service23','service24','service25',
   'service26','service27','service28','service29','service30']
        env.Module = input message: 'what are we deploying today?',ok : 'Deploy',
        parameters:[choice(choices: CHOICES, description: 'Select your service',name: 'TAG')]
        
        docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub_id') {
         dir("${env.Module}"){
        sh "pwd"
        sh 'ls -a'
         } 
            def customImage = docker.build("manibpl0509/trivy" ./${env.Module}/Dockerfile )
        /* Push the container to the custom Registry */
        customImage.push("${env.BUILD_NUMBER}")
        }
          }    
                }
            }
        }
       } 
