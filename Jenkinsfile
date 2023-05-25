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
                bat 'python --version'
                bat 'python -m pip install virtualenv'
                bat 'python -m pip install -r requirements.txt'
            }
        }

        stage('Build') {
            steps {
                echo 'Build Started...'
                /*bat 'python app.py'*/
            }
        }

        stage('Test') {
            steps {
                echo 'Testing Started...'
                bat 'python -m unittest discover tests'
                /*bat 'python -m unittest tests/test_something.py'*/
            }
        }

        stage('Deployment') {
            steps {
                echo 'Deployment Started...'
                bat 'python app.py'
                timeout(time: 2, unit: 'MINUTES')
                echo 'Deployment Completed...'
                if (build.getResult().equals(null)) {
                    build.doKill()
                }
            }
        }
    }
    post {
        /*stage('send email'){
            steps{
                mail bcc: '', body: "<br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> Go to build url and approve the deployment request <br> URL of the build: ${env.BUILD_URL}", cc: '', from: '', replyTo: '', subject: 'email from jenkins', to: '15ucs130@lnmiit.ac.in'
            }
        }*/
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
