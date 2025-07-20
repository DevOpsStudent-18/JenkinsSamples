pipeline{
  agent any

  stages{
    stage("checkout code"){
      steps{
           checkout scm
      }
  }
    stage("Build"){
      steps{
      script{
           sh 'mvn package'
      }
      }

  }


}
}
