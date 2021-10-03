pipeline {
    agent any
    tools {
        maven 'default'
    }
    stages{
        stage('Build'){
            steps {
                bat """
                    mvn clean package
                """
            }
            post {
                success {
                    echo "开始存档..."
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to staging'){
            steps{
                build job: 'deploy-to-staging'
            }
        }
    }
}