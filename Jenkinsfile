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
		     
		 withCredentials([
			usernamePassword(credentialsId: "dockerregistry",usernameVariable: 'username',passwordVariable: 'password')
		]) {
			sh "docker login https://hub.docker.com/ -u ${username} -p ${password}"
		 }
                 
                 if(env.APPNAME == " " || env.APPNAME.contains("-")){
          			print("ERROR: No APPNAME was provided")
		 }else{
                    withCredentials([
	                           file(credentialsId: 'filetext', variable: 'filename')
		    ]){
		    sh 'echo "success" ' 
		    }
                }
         }
        }
    }
}

}
