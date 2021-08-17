
import java.text.SimpleDateFormat

def branch_name = ""
def gitShorthash = ""
def version = ""

class Config {
    
    static imagePath = [
        'develop': 'sandbox',
        'master':  'master'
    ]

    static userCredential = [
        'develop':  'cds-user',
        'master': 'cds-user'
    ]
}




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
                branch_name = env.BRANCH_NAME.toLowerCase()
                image_path = "demo/${Config.imagePath.get(env.BRANCH_NAME)}"
                gitShortHash = getGitShortHash()
                build_number = env.BUILD_ID
                 
                version = "${branch_name}_${build_number}_${gitShortHash}"
                docker_image = "${registry}/${image_path}:${version}"
                print("Docker image: ${docker_image}")
                 
                withCredentials([[$class: 'UP', credentialsId: "user", usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD']]) {
                    sh "docker login $docker_registry -u=\"$USERNAME\" -p=\"$PASSWORD\""
                    sh "docker build -t $docker_image ."
                    sh "docker push $docker_image"
                }
            }
        }
    }
 }
}

