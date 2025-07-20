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
           sh 'java -cp target/jb-hello-world-maven-0.1.0.jar hello.HelloWorld'
      }
      }

  }


}
}
