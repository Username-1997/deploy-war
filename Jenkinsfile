pipeline {
    agent any 
    
   tools { 
        maven 'MAVEN_HOME' 
         }
    stages {
        
        stage('clone repo and clean it') { 
            steps {
                
                 bat "https://github.com/Username-1997/deploy-war.git"
                 bat "mvn clean -f deploy-war"
            }
        
        post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        
        stage('Deploy') { 
            steps {
            deploy adapters: [tomcat8(credentialsId: 'c9ed9716-9079-4df0-8ba1-263f3c20d68f', path: '', url: 'http://localhost:9090/')], contextPath: null, war: '**/*.war'
            }
        
        }
    }
}
