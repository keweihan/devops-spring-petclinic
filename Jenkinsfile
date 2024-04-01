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
        sh 'git clone https://github.com/keweihan/devops-spring-petclinic.git'
        script {
          withSonarQubeEnv('SonarQube Server') {
            sh "/opt/sonar-scanner-5.0.1.3006-linux/bin/sonar-scanner -D sonar.projectKey=devops-spring-petclinic -D sonar.java.binaries=./"
          }
        }

      }
    }

    stage('Run') {
      steps {
        sh 'nohup java -jar target/*.jar'
      }
    }

  }
}