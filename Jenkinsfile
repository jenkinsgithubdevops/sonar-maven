node {
    stage('Code Checkout') { // for display purposes
     echo 'Checout Code and clone it inside jenkins workspace.'
     git 'https://github.com/itrainavengers/sonar-maven.git'
   }
   stage('Build Test & Package') {
      echo 'Build the package'
      withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
       sh 'mvn clean install'
     }
   }
   stage('SonarScan') {
      //withSonarQubeEnv('SonarQube') {
         withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
             //sh 'mvn clean package sonar:sonar' 
             sh 'mvn org.jacoco:jacoco-maven-plugin:prepare-agent package sonar:sonar' +
             ' -Dsonar.projectKey=itrainavengers_sonar-maven '+
             ' -Dsonar.host.url=https://sonarcloud.io '+
             ' -Dsonar.organization=itrainavengers-1 '+ 
             ' -Dsonar.login=a2f06d4685da2eeea7fd1e9261cc45bedbf4f9e5 '   
         //}
      }
   }
   stage('Artifacts') {
       echo 'package the project artifacts..'
       withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
       sh 'mvn package'
     }
   
   }
   stage('Deploy to Dev'){
       echo 'Deploy to Dev environment'
   }
   stage('Deploy to Test'){
       echo 'Deploy to Test environment'
   }
      stage('Test Automation'){
       echo 'Deploy to Dev environment'
   }
   
}
