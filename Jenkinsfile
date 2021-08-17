
pipeline {
    agent any
    stages {
      stage ('download') {
          when { 
            
                  branch 'master'
                 
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

