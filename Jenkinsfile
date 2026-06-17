pipeline {
  agent {
    lable "jenkins-node"
  }

  triggers {
    pollSCM('* * * * *')
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', 
        url: '<URL>'
      }
    }
    stage('Test Application') {
      steps {
        sh 'mvn test'
      }
    }
    stage('Build Application') {
      steps {
        sh 'mvn package -DskipTests=true'
      }
    }
    stage('Application Deploy') {
      steps {
        deploy adapters: [tomcat9(credentialsId: 'tomcat-user', url: 'http://192.168.56.102:8080')], contextPath: null, war: 'target/hello-world.war'
      }
    }
  }
}


