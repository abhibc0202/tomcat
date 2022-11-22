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
                    deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://54.87.128.232:8090/')], contextPath: null, war: '**/*.war'
                    }
                }
            }
   }
}
