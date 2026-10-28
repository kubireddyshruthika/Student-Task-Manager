pipeline {
agent any


stages {
    stage('Build') {
        steps {
            echo 'Building Student Task Manager'
            bat 'if exist index.html (echo Website file found) else (exit 1)'
        }
    }

    stage('Test') {
        steps {
            echo 'Testing Student Task Manager'
            bat 'findstr /C:"Student Task Manager" index.html'
        }
    }

    stage('Deploy') {
        steps {
            echo 'Preparing Student Task Manager for deployment'
            bat 'if exist index.html (echo Deployment files ready) else (exit 1)'
        }
    }
}

post {
    success {
        echo 'Student Task Manager CI/CD pipeline completed successfully!'
    }
}


}