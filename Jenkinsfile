pipeline {
  agent {label "linux"}
  stages{
    stage('hello') {
      steps {
        echo 'hello from Jenkinsfile'
      }
    }
    stage('BUILD: prepare environment'){ 
      when {
        anyOf { branch 'develop'; branch 'mmain' }
      }
      steps {
        echo 'prepare Maven, Java JDK'
        sh 'export JAVA_HOME=/Library/Java/JavaVirtualMachines/adoptopenjdk-8.jdk/Contents/Home'
        sh 'export MAVEN_HOME=/Users/khoahoang/apache-maven-3.8.1'
        sh 'export PATH=$PATH:$MAVEN_HOME/bin'
        echo 'Environment: '
        sh 'mvn --version'
        sh 'java -version'
      }
    }
    stage('DEPLOY: develop'){
      when {
        branch 'develop'
      }
      steps {
        echo 'deploy UAT'
      }
    }
    stage('DEPLOY: main'){
      when {
        branch 'main'
      }
      steps {
        sh 'mvn clean deploy -DmuleDeploy -DskipTests -Dmule.version=4.4.0 -Danypoint.username=khoamule7 -Danypoint.password=123456Aa@ -Denv=Sandbox -Dbusiness=Tiki -DvCore=Micro -Dworkers=1'
      }
    }
  }
}
