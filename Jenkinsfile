pipeline {
  agent {
    docker {
      args '-v /root/.m2:/root/.m2'
      image 'maven:3-alpine'
    }
  }
  stages {
    stage('Build Stage') {
      steps {
        sh label: '', script: 'mvn -B -DskipTests clean package'
      }
    }
    stage('Test Stage') {
            steps {
                sh 'mvn test'
            }
             post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
             }
      }
   }
}
