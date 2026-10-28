pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'BUILD: Checking website files'
                bat 'if exist index.html (echo Website file found) else (exit 1)'
            }
        }

        stage('Test') {
            steps {
                echo 'TEST: Validating website'
                bat 'findstr /I /C:"<html" index.html'
                bat 'findstr /I /C:"<script" index.html'
                echo 'TEST PASSED: HTML and JavaScript sections found'
            }
        }

        stage('Deploy') {
            steps {
                echo 'DEPLOY: Preparing website files'
                bat 'if not exist "%WORKSPACE%\\deployed" mkdir "%WORKSPACE%\\deployed"'
                bat 'copy /Y index.html "%WORKSPACE%\\deployed\\index.html"'
                echo 'DEPLOY SUCCESS: Website copied to deployed folder'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Student Task Manager CI/CD pipeline completed!'
        }
        failure {
            echo 'FAILED: Check the Console Output for details.'
        }
    }
}