pipeline {
  agent {
    docker {
      args '-v /root/.m2:/root/.m2'
      image 'maven:3-alpine'
    }

  }
  stages {
    stage('build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }
    stage('tests') {
      steps {
        junit 'target/surefire-reports/*.xml'
        sh 'mvn test'
      }
    }
  }
}