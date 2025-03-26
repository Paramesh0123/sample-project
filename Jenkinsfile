pipeline {
  agent any 

  stages {
    stage('Hello World') {
      steps {
        sh 'git clone https://github.com/Paramesh0123/sample-project.git'
      }
    }
    stage('build') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage('deploy') {
      steps {
        sshagent(['connection-tomcat-jenkins']) {
          sh "scp -o StrictHostKeyChecking=no target/hello-world-webapp.war ubuntu@13.232.125.170:/home/ubuntu/apache-tomcat-10.1.39/webapps"
        }
      }
    }
  }
}
        
