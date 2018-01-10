pipeline{
  agent any
  tools{
    maven 'mavenLatest'
  }


  stages{
    stage('Build'){
      steps{
       sh 'mvn clean package'
      }
    }
  }
}
