pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'export JAVA_HOME="/usr/lib/jvm/java-1.17.0-openjdk-amd64";./mvnw package'
        sh '''
rm -rf /home/vagrant/pet_builds  && mkdir /home/vagrant/pet_builds && cp target/*.jar /home/vagrant/pet_builds'''
      }
    }

    stage('Ansible') {
      steps {
        ansiblePlaybook(playbook: '/vagrant/playbook.yaml', inventory: '/vagrant/inventory.ini')
      }
    }

  }
}