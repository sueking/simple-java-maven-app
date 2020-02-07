pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh 'mvn -B -DskipTests clean package'
          }
        }

        stage('Test') {
          agent {
            docker {
              image 'maven:3-alpine'
            }

          }
          steps {
            sh 'mvn test'
          }
        }

      }
    }

  }
}