@Library('shared_libraries') _
pipeline {
  agent any 
  stages {
    stage('Hello World') {
      steps {
        checkout_sample_project()
      }
    }
    stage('SonarQube Analysis') {
       withSonarQubeEnv('Sonar-code-check') {
	       sh 'mvn sonar:sonar'
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
          sh "scp -o StrictHostKeyChecking=no target/hello-world-webapp.war ubuntu@35.154.24.43:/home/ubuntu/apache-tomcat-10.1.39/webapps"
        }
      }
    }
  }
}
        
