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
                  sh "/opt/sonar-scanner-5.0.1.3006-linux/bin/sonar-scanner"
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
