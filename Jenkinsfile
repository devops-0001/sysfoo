pipeline {
  agent none
  stages {
    stage('build') {
      agent {
        docker {
          image 'maven:3.6.3-jdk-11-slim'
        }

      }
      steps {
        echo 'building sysfoo app...'
        sh 'mvn compile'
      }
    }

    stage('unit tests') {
      agent {
        docker {
          image 'maven:3.6.3-jdk-11-slim'
        }

      }
      steps {
        echo 'running unit tests'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      agent {
        docker {
          image 'maven:3.6.3-jdk-11-slim'
        }

      }
      steps {
        echo 'generating .war file'
        sh 'mvn package -DskipTests'
        archiveArtifacts '**/target/*.war'
      }
    }

  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}