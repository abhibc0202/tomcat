pipeline {
    agent any;
    stages {
        stage ('git clone') {
            stage ('BUILD') {
        steps {
        git(
        credentialsId: 'git-hub', url: 'https://github.com/abhibc0202/java1.git'
            )
        }
              }
        stage ('Build with maven') {
            stage ('BUILD') {
            steps {
                sh '''
                mvn clean package
                '''
                }
        }
            stage ('deploy') {
                steps {
                    script{
                    deploy adapters: [tomcat9(credentialsId: 'deploy', path: '', url: 'http://52.205.251.136:8090/')], contextPath: 'deploy-to-tomcat', war: '**/*.war'
                    }
                }
            }
   }
}
