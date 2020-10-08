pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
              docker { image 'node:14-alpine' }
            }
            steps {
                // checkout from scm
                // checkout scm
                // show some magic of the container
                sh 'node --version'
                // stash some buildartefacts using "dist" as their qualifier
                stash includes: 'playbook.yaml', name: 'dist'
            }
        }
        stage('Ansible') {
            agent any
            steps {
                // unstash some buildartefacts from a previous stage using "dist" as their qualifier
                // unstash 'dist'
                // show some ansible magic
                sh 'ansible --version'
                sh 'ls -la'
                checkout scm
                sh 'ansible-playbook -i /etc/inventory.yaml playbook.yml'
            }
        }
    }
    post { 
        always { 
            cleanWs()
        }
    }
}
