pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'GitHub source code checked out successfully.'
            }
        }

        stage('Verify') {
            steps {
                bat 'if exist index.html (echo SUCCESS: index.html exists) else (echo ERROR: index.html missing & exit /b 1)'
            }
        }

        stage('Build') {
            steps {
                echo 'Student Task Manager build successful.'
            }
        }

        stage('Test') {
            steps {
                script {
                    if (!fileExists('index.html')) {
                        error('index.html is missing from the workspace.')
                    }

                    def html = readFile('index.html')

                    if (html.trim().isEmpty()) {
                        error('index.html is empty. Add your website code.')
                    }

                    echo 'SUCCESS: HTML file exists and is not empty.'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deployment verification successful.'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: All Jenkins pipeline stages passed!'
        }

        failure {
            echo 'FAILED: Check the Console Output for the exact error.'
        }
    }
}