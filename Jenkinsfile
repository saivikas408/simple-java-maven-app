pipeline {
  agent {
    docker {
      args '-v /root/.m2:/root/.m2'
      image 'maven:3-alpine'
    }
  }
  stages {
    stage('Build') {
      steps {
        sh label: '', script: 'mvn -B -DskipTests clean package'
      }
    }
  }
}
