pipeline {
  agent any 

  stages {
    stage('Hello World') {
      steps {
        sh 'git pull https://github.com/Paramesh0123/sample-project.git'
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
          sh "scp -o StrictHostKeyChecking=no target/hello-world-webapp.war ubuntu@3.7.46.213:/home/ubuntu/apache-tomcat-10.1.39/webapps"
        }
      }
    }
  }
}
        
