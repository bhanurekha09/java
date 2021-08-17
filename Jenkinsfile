
pipeline {
    agent any
stages {
    stage ('download') {
        steps {
            script {
                def scmInfo = checkout scm
                println "GIT_COMMIT " + scmInfo.GIT_COMMIT
            }
        }
    }
}




