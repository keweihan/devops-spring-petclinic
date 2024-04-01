pipeline {
  agent any
  stages {
    
    stage('Build') {
      steps {
        sh 'export JAVA_HOME="/usr/lib/jvm/java-1.17.0-openjdk-amd64";./mvnw package'
      }
    }

    stage('SonarQube analysis') {
      steps {
          script {
              withSonarQubeEnv('SonarQube Server') {
                  sh "<path_to_sonarqube_scanner>/bin/sonar-scanner"
              }
          }
      }
    }

    stage('Run') {
      steps {
        sh 'java -jar target/*.jar'
      }
    }
    

  }
}
