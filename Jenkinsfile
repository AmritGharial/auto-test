pipeline {
    agent any

    environment {
        NODE_VERSION = '18'
    }

    stages {
        stage('Clone Automation Tests Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/AmritGharial/auto-test.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Web Automation Tests') {
            steps {
                sh 'npx wdio wdio.conf.js'
            }
        }
    }

    post {
        success {
            echo '🎉 Web Automation Tests Passed!'
        }
        failure {
            echo '❌ Tests Failed! Check logs.'
        }
    }
}
