pipeline{
  agent none
  tools{
    maven 'mavenLatest'
  }

  options {
    buildDiscarder(logRotator(numToKeepStr: '2', artifactNumToKeepStr: '1'))
  }


  stages{
    stage('Build'){
      agent{
       docker{
        image 'openjdk:8-jre'
        label 'master'
       }
      }
      steps{
       sh 'mvn clean package'
      }
    }
  }
  post{
   always{
    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
    junit 'target/surefire-reports/*.xml'
   }
  }
}
