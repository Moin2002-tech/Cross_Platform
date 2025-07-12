pipeline {
    agent any

    stages {
        stage('Install Build Tools') {
            steps {
                sh 'sudo apt update && sudo apt install -y build-essential cmake'
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Configure') {
            steps {
                sh 'cmake -S . -B build'
            }
        }

        stage('Build') {
            steps {
                sh 'cmake --build build'
            }
        }

        stage('Run') {
            steps {
                sh './build/hello'
            }
        }
    }
}
