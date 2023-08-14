pipeline{
    agent any
    environment {
        PATH = "$PATH:/opt/apache-maven-3.9.4/bin"
    }
    stages{
       stage('GetCode'){
            steps{
                git 'https://github.com/hades1908/official-tomcat.git'
            }
         }        
       stage('Build'){
            steps{
                dir('/var/lib/jenkins/tomcat') {
                sh 'mvn clean package'
               }
            }
         }
        stage('SonarQube analysis') {
        steps{
        withSonarQubeEnv('sonarqube-10.1') { 
        // If you have configured more than one global server connection, you can specify its name
//      sh "${scannerHome}/bin/sonar-scanner"
        sh "mvn sonar:sonar"
    }
        }
        }
       
    }
}
