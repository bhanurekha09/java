import java.text.SimpleDateFormat
import jenkins.model.*

pipeline {
    agent any
    parameters
    {
    string(name: 'RELEASE_VERSION', defaultValue: '2.0.1', description: 'Release version')
    //string(name: 'LATAM_AIRFLOW_VERSION', defaultValue: '2.0.0', description: 'Latam Airflow version')
    //string(name: 'AIRFLOW_UI_PORT', defaultValue: '8089', description: 'Airflow Webserver Local Port')
    // Remember that first option is defaultValue for choices
    choice(name: 'ENVIRONMENT', choices: ['DEV', 'UACC', 'PROD'], description: 'environment')
    choice(name: 'NAMESPACE', choices: ['dev', 'uacc', 'prod'], description: 'namespace')
    }   
    
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
                 print("environment: ${params.ENVIRONMENT}")
                }
         }
        }
    }
 

