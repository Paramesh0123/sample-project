@Library("shared_libraries") _
pipeline {
agent any
stages {
  stage('checkout') {
    steps {
        checkout_sample_project()
    }
  }
  stage('build') {
    steps {
        mavenbuild()
    }
  }
  stage('SonarQube Analysis') {
    steps {
      withSonarQubeEnv('sonar') {
        sh 'mvn sonar:sonar'
      }
    }
  }
  stage('deploy') {
    steps {
      sshagent(['connection-tomcat-jenkins']) {
        sh "scp -o StrictHostKeyChecking=no target/hello-world-webapp.war ubuntu@35.154.24.43:/home/ubuntu/apache-tomcat-10.1.39/webapps"
      }
    }
  }
}
}
