pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'compile maven app'
        sh 'mvn compile'
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            echo 'test maven app'
            sh 'mvn clean test'
          }
        }

        stage('unit test') {
          steps {
            sleep 3
          }
        }

        stage('SCA') {
          steps {
            sleep 1
          }
        }

      }
    }

    stage('package') {
      parallel {
        stage('package') {
          steps {
            echo 'package maven app'
            sh 'mvn package -DskipTests'
          }
        }

        stage('pkg') {
          steps {
            sleep 2
          }
        }

      }
    }

  }
  tools {
    maven 'Maven 3.6.3'
  }
}