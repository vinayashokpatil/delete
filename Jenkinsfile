pipeline {
   agent any
   tools {
     maven 'maven'
   }

   stages{

      stage("Checkout"){
       steps{
         echo "this is taken care using pipelinescript from SCM in Jenkins"
         echo "so no need to add any steps here in Jenkinsfile"
         }
      }
      stage("build using Maven"){
       steps{
         sh 'mvn clean install package'
         }
      }
      stage('Sonarqube') {
         environment {
               scannerHome = tool 'SonarQubeScanner'
         }
      steps {
               withSonarQubeEnv('sonarqube') {
               sh "${scannerHome}/bin/sonar-scanner"
               }
            timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
        }
    }
}
      
      
      
   }
}
