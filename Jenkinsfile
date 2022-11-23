pipeline {
    agent none
    stages {
        stage ('git clone') {
            agent {
  label 'label1'
}
        steps {
        git(
        credentialsId: 'git-hub', url: 'https://github.com/abhibc0202/java1.git'
            )
        }
              }
        stage ('Build with maven') {
            agent {
  label 'label1'
}
            steps {
                sh '''
                mvn clean package
                '''
                }
        }
            stage ('deploy') {
                agent {
  label 'label1'
}
                steps {
                    script{
                    deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://54.87.128.232:8090/')], contextPath: null, war: '**/*.war'
                    }
                }
            }
   }
}
