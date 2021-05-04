node {
    properties([parameters([choice(choices: ['service1', 'service2'], description: '', name: 'Choises')])])
   if (Choises.equals("service1")){
    sh ''' cd service1 '''
   }
   else if (Choices.equals("service2")){
   sh ''' cd service2 '''
}
}
