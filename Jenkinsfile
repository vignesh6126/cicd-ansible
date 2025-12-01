pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')   // poll every 1 minute
    }

    stages {

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
