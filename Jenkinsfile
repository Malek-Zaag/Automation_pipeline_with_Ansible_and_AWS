pipeline {
  agent any
  stages {
    stage('Stage 1') {
      steps {
        echo 'Hello world!'
      }
    }
    stage("getting code") {
      steps {
        echo "======== executing stage ========"
        git url: 'https://github.com/Malek-Zaag/CICD-pipeline-with-Ansible-and-AWS.git', branch: 'main', credentialsId: 'Github-creds'       
        sh "ls -ltr"
        sh "java --version"
      }
    }
  }
}