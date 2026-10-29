
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
                        error('index.html is missing.')
                    }
                    echo 'SUCCESS: index.html exists.'
                }
            }
        }

        stage('Build') {
            steps {
                echo 'Build stage completed successfully.'
            }
        }

        stage('Test') {
            steps {
                bat 'findstr /i /c:"<html" index.html > NUL'
                echo 'SUCCESS: HTML file test passed.'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deployment stage completed.'
                echo 'Website: https://kubireddyshruthika.github.io/Student-Task-Manager/'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: All pipeline stages passed!'
        }
        failure {
            echo 'Pipeline failed. Check the first error above.'
        }
    }
}
