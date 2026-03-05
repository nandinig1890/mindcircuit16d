pipeline {
  agent any 
  
  stages {

     stage('my stage1 - git clone'){
       steps{
          echo 'this is git clone stage'
          git branch: 'main', url: 'https://github.com/nandinig1890/mindcircuit16d.git'      
       }
     }
     stage('my stage2 - artifact build stage by maven'){
       steps{
          echo 'artifact build stage' 
          sh 'mvn clean install'                 
                    
       }
     }
     stage('my stage3 - deployment stage to tomact'){
       steps{
          echo 'deploy artifact to tomcat'   
          deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://ec2-3-91-35-94.compute-1.amazonaws.com:8080')], contextPath: 'my-greeting-holi', war: '**/*.war'               
            
       }
     }
  }
}
