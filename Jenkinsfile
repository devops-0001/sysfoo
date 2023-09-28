pipeline {
  agent any

  tools{
    maven 'Maven 3.6.3'  
  }
  
  stages{
      stage("build"){
          steps{
              echo 'building sysfoo app...'
              sh 'mvn compile'
          }
      }
      stage("test"){
          steps{
              echo 'running unit tests'
              sh 'mvn clean test'
          }
      }
      stage("package"){
          steps{
              echo 'generating .war file'
              sh 'mvn package -DskipTests'
          }
      }
  }

  post{
    always{
        echo 'This pipeline is completed..'
    }
  }
}
