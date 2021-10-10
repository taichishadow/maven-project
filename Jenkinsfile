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
    stages ('Deployments') {
        parallel {
            stage ('Deploy to Production') {
                steps {
                    bat "scp C:/'Program Files'/Jenkins/*.war taichishadow@${params.tomcat_prod}:/opt/tomcat8/webapps/"
                }
            }
        }
    }
}