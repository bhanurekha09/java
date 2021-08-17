
pipeline {
    agent any
    stages {
      stage ('download') {
         steps {
                checkout scm
          }
          post {
              success {
                  updateGitlabCommitStatus name: STAGE_NAME, state: 'success'
              }
              failure {
                  updateGitlabCommitStatus name: STAGE_NAME, state: 'failed'
              }
              aborted {
                  updateGitlabCommitStatus name: STAGE_NAME, state: 'canceled'
              }
    }
 }
}




