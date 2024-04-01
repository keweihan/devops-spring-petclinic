pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'export JAVA_HOME="/usr/lib/jvm/java-1.17.0-openjdk-amd64";./mvnw package'
        withSonarQubeEnv 'test'
      }
    }

    stage('Run') {
      steps {
        sh 'java -jar target/*.jar'
      }
    }

  }
}