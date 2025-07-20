pipeline{
  agent any

  stages{
    stage("checkout code"){
      steps{
           scm checkout
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
