pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'index.html'
            }
        }

        stage('Deploy using Ansible') {
            steps {
                bat """
                wsl ansible-playbook /mnt/c/ProgramData/Jenkins/.jenkins/workspace/cicd-ansible/deploy.yml
                """
            }
        }
    }
}
