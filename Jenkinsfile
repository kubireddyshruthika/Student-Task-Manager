pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify Project Files') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'test -f index.html'
                    } else {
                        bat 'if not exist index.html exit /b 1'
                    }
                }
                echo 'index.html found successfully!'
            }
        }

        stage('Build') {
            steps {
                echo 'Student Task Manager build completed successfully.'
            }
        }

        stage('Test') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'grep -q "<html" index.html'
                    } else {
                        bat 'findstr /i /c:"<html" index.html'
                    }
                }
                echo 'Basic HTML verification passed!'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deployment stage completed. GitHub Pages publishing is separate.'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Student Task Manager pipeline completed!'
        }

        failure {
            echo 'FAILED: Check the Console Output above for the exact error.'
        }
    }
}