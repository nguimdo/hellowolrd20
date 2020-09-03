pipeline {
  agent any
  tools {
    maven 'M2_HOME'
  }
  environment {
     registry = "nguimdofrancine/devops_pip" 
     registryCredential = 'DockerID' 
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
     stage('Building our image') { 
       steps {  
         script { 
                dockerImage = docker.build registry + ":$BUILD_NUMBER"
             }
           }
     }
     stage('Deploy our image') { 
       steps { 
          script {
            checkout scm
            docker.withRegistry( '', registryCredential ) { 
              dockerImage.push("$BUILD_NUMBER")
            }
          }
       }
     }
  }
}

              
              
              
             
           
         
  

             





