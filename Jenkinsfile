pipeline {
    agent any
    triggers { githubPush() }
    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Build') {
            steps { sh 'python3 app.py' }
        }
        stage('Test') {
            steps {
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install pytest
                    python -m pytest -q
                '''
            }
        }
    }
    post {
        success { echo 'Pipeline succeeded' }
        failure { echo 'Pipeline failed' }
    }
}
