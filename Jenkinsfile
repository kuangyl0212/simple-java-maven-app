pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /Users/forest/.m2:/root/.m2'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh '''mvn help:effective-pom
mvn -B -DskipTests clean package'''
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
      }
    }

  }
}