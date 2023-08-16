pipeline {
    agent {
        node {
            label 'maven'
        }
    }
envirnoment {
    PATH =  "/opt/apache-maven-3.9.2/bin:$PATH"
}
    stages {
        stage('build') {
            steps {
                sh 'mvn clean deploy'
            }
        }
    stage('SonarQube analysis') {
    envirnoment {
      scannerHome = tool 'valaxy-sonar-scanner'
    }
    steps {
    withSonarQubeEnv('valaxy-sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
    }
    }
  }    
}
}
