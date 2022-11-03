pipeline {
  agent {label "linux"}
  stages{
    stage('hello') {
      steps {
        echo 'hello from Jenkinsfile'
      }
    }
    stage('for the branch develop'){
      when{
        branch 'develop'
      }
      steps {
        echo 'deploy UAT'
      }
    }
    stage('for the branch main'){
      when{
        branch 'main'
      }
      steps {
        sh 'mvn clean deploy -DmuleDeploy -DskipTests -Dmule.version=4.4.0 -Danypoint.username=khoamule8 -Danypoint.password=123456Aaq -Denv=Sandbox -Dappname=myfirstproject123456789 -Dbusiness=Tiki -DvCore=Micro -Dworkers=1'
      }
    }
  }
}
