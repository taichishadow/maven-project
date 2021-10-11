pipeline {
    agent any
    tools {
        maven 'default'
    }
    parameters {
        string(name: 'tomcat_prod', defaultValue: '35.239.75.187', description: 'Production Server')
    }
    triggers {
        pollSCM('* * * * *')
    }
    stages{
        stage('Build'){
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to Production') {
        steps {
                bat "scp C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\FullyAutomated\\webapp\\target\\webapp.war taichishadow@${params.tomcat_prod}:/opt/tomcat8/webapps/"
            }
        }
    }
    
}