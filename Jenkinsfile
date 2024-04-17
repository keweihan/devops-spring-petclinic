pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'export JAVA_HOME="/usr/lib/jvm/java-1.17.0-openjdk-amd64";./mvnw package'
      }
    }

    stage('Run') {
      steps {
        sh '''
rm -rf ~/pet_builds  && cp target/*.jar ~/pet_builds'''
      }
    }

  }
}