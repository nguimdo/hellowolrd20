pipeline {
  agent any
  tools {
    maven 'M2_HOME'
  }
  
  stages {
     stage('Build') {
       steps {
       sh 'mvn clean'
       sh 'mvn install'
       sh 'mvn package' 
       }
     } 
     stage('test') {
       steps { 
         sh 'mvn test'
       }
     } 
     stage('Deploy our image') { 
       steps { 
          script {
            checkout scm
            docker.withRegistry( '', 'DockerID' ) { 
            def dockerImage = docker.build("francinenguimdo/devops-pip:${env.BUILD_ID}")
            dockerImage.push()
            }
          }
       }
     }
  }
}

              
              
              
             
           
         
  

             





