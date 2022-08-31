pipeline {
    agent any

    stages {
        stage('Molecule') {
            steps {
                sh 'ansible-galaxy install git+https://github.com/Dracula33/ansible-vector.git,main -p .'
                dir('ansible-vector') {
                    sh 'molecule test -s centos_7'
                }
            }
        }
    }
}
