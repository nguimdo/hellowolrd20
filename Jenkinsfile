pipeline {
  agent any
  tools {
    maven 'M2_HOME'
  }
  environment {
     registry = "nguimdofrancine/devops_pip" 
     registryCredential = 'DockerRegistry' 
     dockerImage = ''
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
         echo "test Step"
         sh 'mvn test'
       }
     } 
     stage('Deploy our image') { 
       steps { 
          script {
            checkout scm
            docker.withRegistry( '', DockerRegistry ) { 
              dockerImage = docker.build("francinenguimdo/devops-pip:${env.BUILD_ID}")
              dockerImage.push()
            }
          }
       }
     }
  }
}

              
              
              
             
           
         
  

             





