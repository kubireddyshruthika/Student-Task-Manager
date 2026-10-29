
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
                echo '======================================'
                echo 'STUDENT TASK MANAGER DEPLOYMENT'
                echo '======================================'
                echo 'Website URL:'
                echo 'https://kubireddyshruthika.github.io/Student-Task-Manager/'
                echo 'Deployment stage completed.'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: ALL PIPELINE STAGES PASSED!'
            echo 'Open your website:'
            echo 'https://kubireddyshruthika.github.io/Student-Task-Manager/'
        }

        failure {
            echo 'PIPELINE FAILED. Check the Console Output.'
        }
    }
}