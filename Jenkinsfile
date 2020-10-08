pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
              docker { image 'node:14-alpine' }
            }
            steps {
                // show some magic of the container
                sh 'node --version'
                // stash some buildartefacts using "dist" as their qualifier
                // stash includes: 'playbook.yaml', name: 'dist'
            }
        }
        stage('Ansible') {
            agent none
            steps {
                // unstash some buildartefacts from a previous stage using "dist" as their qualifier
                // show some ansible magic
                sh 'ansible --version'
            }
        }
    }
}
