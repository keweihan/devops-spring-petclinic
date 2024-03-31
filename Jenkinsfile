pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''pwd
./mvnw package
java -jar target/*.jar'''
      }
    }

  }
}