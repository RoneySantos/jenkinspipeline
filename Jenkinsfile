// Jenkinsfile (Declarative Pipeline)
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                cd /etc
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
//    post {
//        always {
//            slackNotifier(currentBuild.currentResult)
//            cleanWs()
//        }
//    }
        stage('Notificando o usuario') {
            steps {
//            slackSend (color: 'error', message: "Build Started - ${env.EXECUTOR_NUMBER} ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'slack_token')  
            slackSend failOnError: true, message: "Build Started - ${env.EXECUTOR_NUMBER} ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'slack_token'  
//              slackSend (color: 'error', message: '[ Sucesso ] O novo build esta disponivel em: http://192.168.33.10:81/ ', tokenCredentialId: 'slack_token')
//              slackSend "Build Started - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
            }
        }
    }
}
