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
                slackSend (color: 'good', message: '[ Sucesso ] Teste realizado com sucesso ', tokenCredentialId: 'slack-token')
            }
        }
    }
}
