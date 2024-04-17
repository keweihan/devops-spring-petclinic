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
      environment {
        INVENTORY = '/vagrant/inventory.ini'
        PLAYBOOK = '/vagrant/playbook.yaml'
        PRIVATE_KEY = '/home/vagrant/.ssh/id_rsa'
      }
      steps {
        ansiblePlaybook(disableHostKeyChecking: true, playbook: '/vagrant/playbook.yaml', inventory: '/vagrant/inventory.ini', credentialsId: '9f1fb59e-ab34-42f5-add9-2c5353e5d3ae')
      }
    }

  }
}