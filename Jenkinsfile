node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def mvn = tool 'Default Maven';
    withSonarQubeEnv('sonarqube-10.1') {
      sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=tomcat -Dsonar.projectName='tomcat'"
    }
  }
}
