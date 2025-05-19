pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                bat 'git clone https://github.com/Niroshan00/8.2CDevSecOp.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test || exit 0' // Allows pipeline to continue despite test failures
            }
        }

        stage('Generate Coverage Report') {
            steps {
                rem Ensure coverage report exists
                bat 'npm run coverage || exit 0'
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                bat 'npm audit || exit 0' // This will show known CVEs in the output
            }
        }
    }
}
