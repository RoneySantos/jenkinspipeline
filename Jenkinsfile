stage 'Checkout'
  node() {
      deleteDir()
      checkout scm
  }

stage 'Build & Archive Apk'
node () {
    sh 'export ANDROID_SERIAL=10.0.3.15:5555 ; .build.sh'
    step([$class: 'ArtifactArchiver', artifacts: 'meu_aplicativo/build/outputs/apk/meu_aplicativo.apk'])
}
post {
    failure {
        slackSend failOnError:true message:"Build failed  - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
    }
