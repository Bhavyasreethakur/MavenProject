pipeline {
    agent any 
    environment {
        mvn_Home = tool name: 'maven', type: 'maven'
    }
 stages {
        stage('Clone') { 	
            steps {
                sh "rm -rf MavenProject"
                sh "git clone https://github.com/Bhavyasreethakur/MavenProject.git"
                sh "${mvn_Home}/bin/mvn clean"
            }
        }
        stage('Test') {
            steps {
               sh "${mvn_Home}/bin/mvn test" 
            }
        }
        stage('Deploy'){
            steps{
              sh "${mvn_Home}/bin/mvn package"  
            }
        }
     stage('email Notification')
     {
         mail bcc: '', body: 'Welcome to Jenkins', cc: '', from: '', replyTo: '', subject: 'job notification', to: 'bhavyasreethakur21@gmail.com'
     }
    } }

