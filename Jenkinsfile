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
     stage('SonarQube Analysis'){
         steps{
             withSonarQubeEnv('sonarqube-server'){
                 sh "${mvn_Home}/bin/mvn sonar:sonar"
             }
         }
     }
     stage("Quality Gate") {
            steps {
              timeout(time: 1, unit: 'HOURS') {
                waitForQualityGate abortPipeline: true
              }
            }
          }
     stage('email Notification')
     {
         steps{
         mail bcc: '', body: 'Welcome to Jenkins', cc: '', from: '', replyTo: '', subject: 'job notification', to: 'bhavyasreethakur21@gmail.com'
         }
         }
    } }

