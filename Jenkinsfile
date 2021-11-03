// Jenkinsfile (Declarative Pipeline)
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
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
        stage('Notificando o usuario') {
            steps {
//                slackSend "Build Started - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
                slackSend (color: 'good', message: "Build Teste - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'slack_token')  
//                slackSend (failOnError: true, message: "Build Failed - ${env.EXECUTOR_NUMBER} ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'slack_token')
//              slackSend (color: 'good', message: '[ Sucesso ] O novo build esta disponivel em: http://192.168.33.10:81/ ', tokenCredentialId: 'slack_token')
            }
        }
    }
}
