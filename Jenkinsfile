pipeline{
  agent any
  tools{
    maven 'mavenLatest'
  }

  options {
    buildDiscarder(logRotator(numToKeepStr: '2', artifactNumToKeepStr: '1'))
  }


  stages{
    stage('Build'){
      steps{
       sh 'mvn clean package'
      }
    }
  }
  post{
   always{
    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
   }
   always {
    junit 'target/surefire-reports/*.xml'
   }
  }
}
