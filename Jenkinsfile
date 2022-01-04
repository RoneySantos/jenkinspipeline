// Jenkinsfile (Declarative Pipeline)
pipeline {
      agent any  

    stages {
        stage('Build') {
            steps {
                sh 'mkdrir lab-teste-jenkins'
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                sh 'ls -la'                       
            }
        }
        stage('Deploy') {
            steps {
                sh 'rm -rf lab-teste-jenkins'
                echo 'Deploying....'
            }
        }
    }
    post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeded!'
              slackSend (color: 'good', message: "The pipeline ${currentBuild.fullDisplayName} completed successfully.")
        }
        unstable {
            echo 'I am unstable :/' //write message in the log file
            slackSend (color: 'warning', message: "The pipeline ${currentBuild.fullDisplayName} is unstable.")
        }
        failure {
            echo 'I failed :('
            slackSend (color: 'danger', message: "Build Failed - ${env.EXECUTOR_NUMBER} ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>).")
              script{
                    def userId = slackUserIdFromEmail('jonissonfn@gmail.com')
                    slackSend(channel: "@$userId", color: "good", message: "The pipeline ${currentBuild.fullDisplayName} completed successfully.")
              }
        }
        changed {
            echo 'Things were different before...'
        }
    }
}
