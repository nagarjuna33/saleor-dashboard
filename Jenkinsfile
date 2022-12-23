pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git branch: 'dev', url: 'https://github.com/WorkshopsByKhaja/saleor-dashboard.git'
            }
        }
        stage('docker image build') {
            steps {
                sh 'docker image build -t nagarjunaduggireddy/saleor-dashboar:DEV .'
            }
        }
        stage('push image to registry') {
            steps {
                sh 'docker image push nagarjunaduggireddy/saleor-dashboar:DEV'
            }
        }
         stage('aks setup') {
            steps {
                sh 'git clone https://github.com/hashicorp/learn-terraform-provision-eks-cluster'
                sh ' terraform init && terraform apply -auto-approve '
            }
        }
    }
}
