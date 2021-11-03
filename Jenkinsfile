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
            steps {3
                echo 'Deploying....'
            }
        }
//    post {
//        always {
//            slackNotifier(currentBuild.currentResult)
//            cleanWs()
//        }
//    }
//      stage('Notificando o usuario') {
//            steps {
//            slackSend (color: 'error', message: "Build Started - ${env.EXECUTOR_NUMBER} ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'slack_token')  
//            slackSend (failOnError: true, message: "Build Fail - ${env.EXECUTOR_NUMBER} ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)", tokenCredentialId: 'slack_token')
//              slackSend (color: 'error', message: '[ Sucesso ] O novo build esta disponivel em: http://192.168.33.10:81/ ', tokenCredentialId: 'slack_token')
//              slackSend "Build Started - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
//            }
        }
    }
}

def sendSlackNotifcation() 
{ 
	if ( currentBuild.currentResult == "SUCCESS" ) {
		buildSummary = "Job:  ${env.JOB_NAME}\n Status: *SUCCESS*\n Build Report: ${env.BUILD_URL}CI-Build-HTML-Report"

		slackSend color : "good", message: "${buildSummary}", channel: '#test-ci-alerts'
		}
	else {
		buildSummary = "Job:  ${env.JOB_NAME}\n Status: *FAILURE*\n Error description: *${CI_ERROR}* \nBuild Report :${env.BUILD_URL}CI-Build-HTML-Report"
		slackSend color : "danger", message: "${buildSummary}", channel: '#test-ci-alerts'
		}
}
