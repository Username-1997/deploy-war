pipeline{
    agent any
    tools{
        maven 'mvn'
    }
    stages{
        stage ('Build'){
            steps{
                bat 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{
                deploy adapters: [tomcat8(credentialsId: 'c9ed9716-9079-4df0-8ba1-263f3c20d68f', path: '', url: 'http://localhost:9090/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
