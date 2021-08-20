import java.text.SimpleDateFormat
import jenkins.model.*

pipeline {
    agent any
    parameters
    {
    string(name: 'APPNAME', defaultValue: '2.0.1')
    //string(name: 'LATAM_AIRFLOW_VERSION', defaultValue: '2.0.0', description: 'Latam Airflow version')
    //string(name: 'AIRFLOW_UI_PORT', defaultValue: '8089', description: 'Airflow Webserver Local Port')
    // Remember that first option is defaultValue for choices
    choice(name: 'ENVIRONMENT', choices: ['DEV', 'UACC', 'PROD'], description: 'environment')
    choice(name: 'NAMESPACE', choices: ['devops', 'dev', 'uacc', 'prod'], description: 'namespace')
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
                 print( "${params.NAMESPACE}")
                 print("${params.APPNAME}")
                 print("${env.APPNAME}")
                 
                 if(env.APPNAME == " " || env.APPNAME.contains("-")){
          			print("ERROR: No APPNAME was provided")
		 }
                 withCredentials([[$file: 'filecredentials', credentialsId: 'filetext', variable: 'filename']])
			 
                     
		 }		 

                }
         }
        }
    }
}

