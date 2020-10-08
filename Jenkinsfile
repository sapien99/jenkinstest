pipeline {
    agent {
        docker { image 'node:14-alpine' }
    }
    stages {
        stage('Build') {
            steps {
                // show some magic of the container
                sh 'node --version'
                stash includes: 'playbook.yaml', name: 'dist'
            }
        }
        stage('Ansible') {
            agent none
            steps {
                unstash 'dist'
                // show some ansible magic
                sh 'ansible --version'
            }
        }
    }
}
