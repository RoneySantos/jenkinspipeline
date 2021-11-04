// Jenkinsfile (Declarative Pipeline)
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
                sh 'node --version'
                slackSend (color: 'good', message: "Testing - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'slack_token')
                           
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
//                slackSend (failOnError: true, message: "Build Failed - ${env.EXECUTOR_NUMBER} ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'slack_token')
//              slackSend (color: 'good', message: '[ Sucesso ] O novo build esta disponivel em: http://192.168.33.10:81/ ', tokenCredentialId: 'slack_token')
            }
        }
    }
    post { // write in the log file
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeded!'
            slackSend (color: 'good', message: "The pipeline ${currentBuild.fullDisplayName} completed successfully.", tokenCredentialId: 'slack_token') //if passed send menssage in the slack
        }
        unstable {
            echo 'I am unstable :/' //write message in the log file
        }
        failure {
            echo 'I failed :('
            slackSend (color: 'danger', message: "The pipeline ${currentBuild.fullDisplayName}  failed.", tokenCredentialId: 'slack_token') // if fail send message in the slack
        }
        changed {
            echo 'Things were different before...'  //write message in the log file
        }
    }    
}