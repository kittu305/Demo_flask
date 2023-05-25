pipeline {
    agent any

    stages {
        /*stage('Checkout') {
            steps {
                git credentialsId: 'jenkins', url: 'https://github.com/blueed/NodejsConsoleApp1.git'
            }
        }*/
        stage('Install dependencies') {
            steps {
                echo 'Installing dependencies...'
                bat 'pip install -r requirements.txt'
                bat 'python app.py'
            }
        }

        stage('Build') {
            steps {
                echo 'Build Started...'
                bat 'python app.py'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing Started...'
                bat 'python -m unittest discover tests'
            }
        }

        stage('Deployment') {
            steps {
                echo 'Deployment Started...'
            }
        }
    }
    post {
        /*always {
            echo 'We came to an end!'
            archiveArtifacts artifacts: 'dist/*.exe', fingerprint: true
            junit 'test-reports/*.xml'
        }*/   
        success {
            echo 'Build successful...'

            // Add any additional post-build actions here
        }
        
        failure {
            echo 'Build failed... :('
        }
    }
}