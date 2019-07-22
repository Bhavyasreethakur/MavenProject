node {
   stage('Clone')
   { 
   git 'https://github.com/Bhavyasreethakur/MavenProject.git'
   }
   stage('clean')
   {
   def mvnHome = tool name: 'maven', type: 'maven'
   sh "${mvnHome}/bin/mvn clean"
   }
   stage('test')
   {
      sh "${mvnHome}/bin/mvn test"
   }
   }
