pipeline {
    agent any
    parameters {
        booleanParam(name: 'SEND_EMAIL', defaultValue: false, description: 'Check to send email notification')
    }
    environment {
        APP_NAME = 'MyApp'
        APP_VERSION = '1.0.0'
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
            }
        }
        stage('Build') {
            steps {
                echo "Compiling application: ${env.APP_NAME} v${env.APP_VERSION}"
                sh 'python3 -m py_compile app.py'
            }
        }
        stage('Send Notification') {
            when {
                expression { params.SEND_EMAIL == true }
            }
            steps {
                echo "Sending email notification for ${env.APP_NAME} v${env.APP_VERSION}..."
            }
        }
    }
}
