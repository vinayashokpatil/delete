pipeline {
   agent any
   tools {
     maven 'maven'
   }
   environment {
      def mvnHome =  tool name: 'maven', type: 'maven'
   }
   stages{

      stage("Checkout"){
       steps{
         echo "this is taken care using pipelinescript from SCM in Jenkins"
         echo "so no need to add any steps here in Jenkinsfile"
         git 'https://github.com/vinayashokpatil/delete.git'
         }
      }
      stage("build using Maven"){
       steps{
         sh 'mvn clean install package'
         }
      }
      
      
    //stage('SonarQube Analysis') {
     //steps {
        //echo "maven home is ${mvnHome}"
       // withSonarQubeEnv('sonarqube') { 
          //sh "${mvnHome}/bin/mvn sonar:sonar"
       // }
       // }
   // }    
      
      stage('SonarQube Analysis') {
     steps {
        echo "maven home is ${mvnHome}"
        withSonarQubeEnv('sonarqube') { 
          sh "sonar:sonar"
        }
        }
    }    
      
   }
}
