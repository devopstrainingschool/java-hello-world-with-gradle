pipeline {
  agent any
  tools {
    gradle "javagradle"
  }
  stages {
    stage ('Maven clean') {
      steps {
      sh 'gradle clean'
      }
  
    }
    
    stage ("Maven package") {
      steps {
      sh 'gradle build'
      }
    
    } 
    
    stage ('Docker build') {
      steps {
      
      sh 'docker build -t devopstrainingschool/jenkins-java-maven .'
      
      }   
    }
   
    stage ('Docker login and push') {
      steps {
        withDockerRegistry([ credentialsId: "Docker_hub", url: "https://index.docker.io/v1/" ]) {
          sh 'docker push devopstrainingschool/jenkins-java-maven'
        }
      }
    }
    
    
    
    
    
    
  }
  
  













}
