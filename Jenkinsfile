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
                echo 'TEST: Checking website file'
                bat 'if exist index.html (echo Test passed) else (exit 1)'
            }
        }

        stage('Deploy') {
            steps {
                echo 'DEPLOY: Copying website'
                bat 'if not exist deployed mkdir deployed'
                bat 'copy /Y index.html deployed\\index.html'
                echo 'DEPLOY SUCCESS'
            }
        }
    }

    post {
        success {
            echo 'Student Task Manager CI/CD pipeline completed successfully!'
        }
    }
}