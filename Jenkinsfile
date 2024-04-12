pipeline {
    agent any
    stages {
        stage('Start up') {
            steps {
            		slackSend(
            	     		color: '#00a00d',
                			message: "[*${currentBuild.fullDisplayName}*] Setting up",
            			    channel:"#devops-team"
            		)
              }
        }

        

        stage('Deploy approval'){
          steps {
            input "Deploy to production?"

            }
        }
    }


    post {
        always {

            slackSend(
                  color: '#00a00d',
                  message: "[*${currentBuild.fullDisplayName}*] ends",
                  channel:"#devops-team"
            )

        }
        success {

            slackSend(
                  color: '#00a00d',
                  message: "[*${currentBuild.fullDisplayName}*] succeeeded",
                  channel:"#devops-team"
            )
        }
        unstable {

            slackSend(
                  color: 'danger',
                  message: "[*${currentBuild.fullDisplayName}*] unstable",
                  channel:"#devops-team"
            )
        }
        failure {

            slackSend(
                  color: 'danger',
                  message: "[*${currentBuild.fullDisplayName}*] failed",
                  channel:"#devops-team"
            )
        }
        changed {
            echo 'Things were different before...'
        }
    }
}
