
pipeline {
    agent any
    stages {
      stage ('download') {
          when { 
              anyOf {
                  branch 'master';
                  branch 'feature';
              }
          }   
         steps {
             script {
                def scmInfo = checkout scm
                println "GIT_COMMIT " + scmInfo.GIT_COMMIT
            }
        }
    }
 }
}

