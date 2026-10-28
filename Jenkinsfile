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
                bat 'if exist index.html (echo Test passed: HTML file exists) else (exit 1)'
                echo 'TEST PASSED!'
            }
        }

        stage('Deploy') {
            steps {
                echo 'DEPLOY: Preparing website files'
                bat 'if not exist deployed mkdir deployed'
                bat 'copy /Y index.html deployed\\index.html'
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