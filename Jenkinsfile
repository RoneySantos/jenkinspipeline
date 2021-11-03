pipeline {
    agent {
        docker { image 'node:14-alpine' }
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                slackSend (color: 'good', message: "Building - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'slack_token')  
            }
        }
        stage('Test') {
            steps {
                sh 'node --versionn'
                def slackResponse = slackSend(color: 'good', message: "Started Building", tokenCredentialId: 'slack_token')
                slackSend(color: 'good', message: "Build still in progress", tokenCredentialId: 'slack_token')
                slackSend(
                    replyBroadcast: true,
                    message: "Build failed. Broadcast to channel for better visibility.",
                    tokenCredentialId: 'slack_token'
                )                           
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                slackSend (color: 'good', message: "Deploying - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'slack_token')  
            }
        }
        stage('Notificando o usuario') {
            steps {
//                slackSend "Build Started - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
                slackSend (color: 'good', message: "Finish - ${env.JOB_NAME} ${env.BUILD_NUMBER} ${env.CHANGE_AUTHOR} ${env.CHANGE_AUTHOR_DISPLAY_NAME} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'slack_token')  
                slackSend (failOnError: true, message: "Build Failed - ${env.EXECUTOR_NUMBER} ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'slack_token')
//              slackSend (color: 'good', message: '[ Sucesso ] O novo build esta disponivel em: http://192.168.33.10:81/ ', tokenCredentialId: 'slack_token')
            }
        }
    }
}
