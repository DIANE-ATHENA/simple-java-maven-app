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
        sh 'mvn test'
        junit 'target/surefire-reports/*.xml'
      }
    }
    stage('informe') {
      steps {
        emailext(subject: 'Haloha', body: 'Haloha', from: 'LAPIN@ubuntu.com', to: 'maryse.ruas@gmail.com')
      }
    }
    stage('AnalyserSonarQube') {
      steps {
        waitForQualityGate()
      }
    }
  }
}