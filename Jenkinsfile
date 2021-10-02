pipeline {
    agent any
    tools {
        maven 'default'
    }
    stages{
        stage('Build'){
            steps {
                bat "C:\Program Files\apache-maven-3.8.2\bin mvn clean package"
            }
            post {
                success {
                    echo "开始存档..."
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}