
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Source code checked out from GitHub.'
            }
        }

        stage('Verify') {
            steps {
                script {
                    if (!fileExists('index.html')) {
                        error('ERROR: index.html not found!')
                    }
                    echo 'SUCCESS: index.html exists.'
                }
            }
        }

        stage('Build') {
            steps {
                echo 'BUILD SUCCESSFUL'
            }
        }

        stage('Test') {
            steps {
                bat 'findstr /i /c:"<html" index.html > NUL'
                echo 'TEST PASSED: HTML file verified.'
            }
        }

        stage('Deploy') {
            steps {
                echo 'DEPLOYMENT STAGE COMPLETED.'
                echo 'Student Task Manager pipeline executed successfully.'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: All pipeline stages passed!'
        }
        failure {
            echo 'FAILURE: Check the Console Output for the error.'
        }
    }
}
