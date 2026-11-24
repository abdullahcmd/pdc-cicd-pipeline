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
            steps { sh 'python3 -m pip install pytest --break-system-packages || true; python3 -m pytest -q' }
        }
    }
    post {
        success { echo 'Pipeline succeeded' }
        failure { echo 'Pipeline failed' }
    }
}
