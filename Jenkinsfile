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
        sh 'ansible-playbook -i $INVENTORY $PLAYBOOK --private-key $PRIVATE_KEY'
      }
    }

  }
}