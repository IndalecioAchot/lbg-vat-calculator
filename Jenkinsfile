pipeline{
agent by
 
stages{
  stage('Checkout') {
     steps {
    //Get some code from a Github repository
    git branch: 'main', url:'https://github.com/IndalecioAchot/lbg-vat-calculator'
     } 
}
  stage('SonarQube Analysis'){
    environment {
      scannerHome = tool 'sonarqube'
    }
      steps{
        withSonarQubeEnv('sonar-qube-1'){
              sh "${scannerHome}/bin/sonar-scanner"
       }
      }

    
  }
 
 
}
 
 
}
