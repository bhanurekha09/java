
pipeline {
  agent { label ('master') }
  triggers {
    gitlab(triggerOnPush: true,
           triggerOnMergeRequest: true,
           branchFilterType: 'ALL')
  }
  
  options {
        gitlabBuilds(builds: ['Importing library', 'Build Artifacts', 'Build Docker Image', 'Deploy'])
        ansicolor('xterm')
        gitLabConnection('https://github.com/bhanurekha09/java')
        disableConcurrentBuilds()
  }









