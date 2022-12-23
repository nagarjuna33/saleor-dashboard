pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git branch: 'main', url: 'https://github.com/WorkshopsByKhaja/saleor-dashboard.git'
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
                sh ' terraform init && terraform apply -auto-approve '
            }
        }
    }
}
