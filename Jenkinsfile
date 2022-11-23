pipeline {
    agent none;
    stages {
        stage ('git clone') {
            agent {
  label 'label2'
}
        steps {
            git(
            credentialsId: 'git-hub', url: 'https://github.com/abhibc0202/javapvt.git'
            )
        }
    }
stage ('Build with maven') {
    agent {
  label 'label2'
}
            steps {
                sh '''
                mvn clean package
                '''
            }
}
    stage ('deploy') {
       agent {
  label 'label2'
} 
   steps {
         script{
         deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://54.88.150.118:8080/')], contextPath: null, war: '**/*.war'
               }
         }    
    }
    }
}
