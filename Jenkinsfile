pipeline {
    agent {
        label 'centos7'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: '1ec9ad8e-7eeb-4307-bf9e-ada8e8efd30c', url: 'https://github.com/alexeiemelin/vector-molecule.git'
            }
        }

        stage('Run sh') {
            steps {
                dir('vector-role') {
                    sh 'pip3 install --user "molecule==3.4.0" "molecule_docker"'
                }
            }
        }
        stage('Molecule version') {
            steps {
                sh 'molecule --version'
            }
        }

        stage('Molecule test') {
            steps {
                dir('vector-role') {
                    sh 'molecule test -s default'
                }
            }
        }
    }
}