pipeline{
agent any
tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }
stages{
  stage('Checkout') {
     steps {
    //Get some code from a Github repository
    git branch: 'main', url:'https://github.com/IndalecioAchot/lbg-vat-calculator.git'
     } 
}
        stage('Checkout Mvn') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', url: 'https://github.com/IndalecioAchot/lbg-hello-world-maven.git'
            }
        }
        stage('Compile') {
            steps {
                // Run Maven on a Unix agent
                sh "mvn clean compile"
            }
        }
        stage('Test') {
            steps {
                sh "mvn test"
            }
        }
          stage('Package') {
            steps {
                sh "mvn -Dmaven.test.skip package"
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
       timeout(time: 10, unit: 'MINUTES'){
          waitForQualityGate abortPipeline: true
        }
      }    
    }
    } 
}

