pipeline {
    agent any

    stages {
        stage('Verify Git Checkout') {
            steps {
                sh 'git rev-parse --short HEAD'
                sh 'git log -1 --oneline'
            }
        }

        stage('Verify Application Files') {
            steps {
                sh 'test -f index.html'
                sh 'cat index.html'
                sh 'echo "Application files found."'
            }
        }

        stage('Build Verification') {
            steps {
                sh 'grep -q "Git and Jenkins Integration Successful" index.html'
                sh 'echo "Build verification passed."'
            }
        }
    }

    post {
        success {
            echo 'SET 11 PASSED: Jenkins successfully retrieved and verified the GitHub project.'
        }
        failure {
            echo 'SET 11 FAILED: Check the Console Output.'
        }
    }
}
