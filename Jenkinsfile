node {
   def mvnHome = tool name: 'maven', type: 'maven'
   stage('Clone')
   { 
   git 'https://github.com/Bhavyasreethakur/MavenProject.git'
   }
   stage('clean')
   {
   
   sh "${mvnHome}/bin/mvn clean"
   }
   stage('test')
   {
      sh "${mvnHome}/bin/mvn test"
   }
    stage('Deploy')
   {
      sh "${mvnHome}/bin/mvn package"
   }
   }
