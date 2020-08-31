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
        echo "test Step"
        sh 'mvn test'
       }
     } 
       stage('deploy') {
       steps {
        echo "deploy Step"
       }
     } 
       stage('docker') {
       steps {
        echo "image Step"
        sleep 10
       }
     } 
   }
}
