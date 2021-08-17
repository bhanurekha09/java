
pipeline {
    agent any
    stages {
      stage ('download') {
          when { 
              anyOf {
                  branch 'master';
                  branch 'feature1';
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

