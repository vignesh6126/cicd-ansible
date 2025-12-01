pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')   // poll every 1 minute
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/<username>/<repo>.git'
            }
        }

        stage('Build') {
            steps {
                echo "Static HTML project - no build required"
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'index.html', fingerprint: true
            }
        }

        stage('Deploy using Ansible') {
            steps {
                sh '''
                ansible-playbook deploy.yml
                '''
            }
        }
    }
}
