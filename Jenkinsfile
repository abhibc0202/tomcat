pipeline{
    agent{
        label 'label2'
    }
    stages{
        stage('CLONING REPO'){
            steps{
                git credentialsId: 'git-hub', url: 'https://github.com/abhibc0202/hello-world.git'
            }
        }    
            stage('BUILD'){
                steps{
                  sh 'mvn clean install'  
                }
            }
            stage('DEPLOYING'){
                steps{
                     echo "archiving"
                        archiveArtifacts artifacts: '**/*.war', followSymlinks: false
                }
                post{
                    success{
                        deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://54.88.150.118:8080')], contextPath: null, war: '**/*.war'
                    }
                }
            }
}
