pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat '"C:\\Users\\DELL\\AppData\\Local\\Programs\\Python\\Python310\\python.exe" -m venv venv'
                bat 'venv\\Scripts\\pip.exe install --upgrade pip'
                bat 'venv\\Scripts\\pip.exe install -r requirements.txt pytest'
            }
        }

        stage('Test') {
            steps {
                bat 'venv\\Scripts\\python.exe -m pytest'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to staging...'
            }
        }
    }

    post {
        success {
            mail to: 'sanidhyasaga@gmail.com',
                 subject: "Build Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Build succeeded. Check Jenkins for details."
        }
        failure {
            mail to: 'sanidhyasaga@gmail.com',
                 subject: "Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Build failed. Check Jenkins logs for errors."
        }
    }
}
