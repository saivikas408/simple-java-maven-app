pipeline {
  agent {
    docker {
      args '-v /root/.m2:/root/.m2'
      image 'maven:3-alpine'
    }

  }
  stages {
    stage('Build Stage') {
      agent {
        docker {
          image 'maven:3-alpine'
        }

      }
      steps {
        sh 'mvn -B -DskipTests clean package'
        sh 'echo \'hi\''
      }
    }
    stage('Test Stage') {
      post {
        always {
          junit 'target/surefire-reports/*.xml'

        }

      }
      steps {
        sh 'mvn test'
      }
    }
    stage('Deliver Stage - delevopment ') {
		when {
            branch 'prod' 
        }
      steps {
		echo 'developemnt'
        sh './jenkins/scripts/deliver.sh'
      }
    }
	stage('Deliver Stage - production ') {
		when {
            branch 'prod' 
        }
      steps {
		echo 'production'
        sh './jenkins/scripts/deliver.sh'
      }
    }
  }
}
