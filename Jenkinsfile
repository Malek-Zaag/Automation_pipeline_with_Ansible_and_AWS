pipeline {
  agent any
  stages {
    stage('Stage 1') {
      steps {
        echo "======== executing stage ========"
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

    stage("checking terraform and provisionning servers") {
        steps {
            echo "======== executing stage ========"
            sh "terraform --version"
            dir ("./Infrastructure/EC2/") {
                sh "terraform init --upgrade"
                
            }

            dir ("./Infrastructure/EC2/") {
              //sh "terraform apply --auto-approve"
            }
        }
    }

    stage ("Adding public IPs to /etc/hosts") {
      steps {
        dir ("./Infrastructure/EC2/") {
              sh "terraform output > file.txt"
              sh "cut -d '=' -f 2 file.txt"
              sh "sudo sed 's/\"//g; s/=//g' file.txt >> /etc/hosts "
            }
      }
    }

    stage("applying ansible playbooks for configuring files") {
       steps {
           echo "======== executing stage ========"
           sh "ansible --version"        
      }
    }
  }
}