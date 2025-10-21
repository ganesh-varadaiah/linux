pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'github_creds', url: 'https://github.com/<username>/<repo>.git'
            }
        }
        stage('Deploy with Ansible') {
            steps {
                sshagent(['ansible_ssh']) {
                    sh 'ansible-playbook -i /etc/ansible/hosts playbook.yml'
                }
            }
        }
    }
}
