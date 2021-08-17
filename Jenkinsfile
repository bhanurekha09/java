def branch_name = ""
def gitShorthash = ""
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
                branch_name = env.BRANCH_NAME>toLowerCase()
                image_path = "demo/${config.imagePath.get(env.BRANCH_NAME)}"
                gitShortHash = getGitShortHash()
                build_number = env.BUILD_ID
                 
                version = "${branch_name}_${build_number}_${gitShortHash}"
                docker_image = "${registry}/${image_path}:${version}"
                print("Docker image: ${docker_image}")
                 
                withCredentials([[$class: 'UP', credentialsId: "cds-user", usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD']]) {
                    sh "docker login $docker_registry -u=\
            }
        }
    }
 }
}

