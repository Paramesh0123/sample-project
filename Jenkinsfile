@Library('shared_libraries') _
pipeline {
  agent any 
  stages {
    stage('Hello World') {
      steps {
        checkout_sample_project()
      }
    }
    stage('compile') {
      steps {
        mavenbuild()
      }
    }
    stage('package') {
      steps {
        mavenbuild()
      }
    }
    stage('deploy') {
      steps {
        sshagent(['connection-tomcat-jenkins']) {
          sh "scp -o StrictHostKeyChecking=no target/hello-world-webapp.war ubuntu@3.7.46.213:/home/ubuntu/apache-tomcat-10.1.39/webapps"
        }
      }
    }
  }
}
        
