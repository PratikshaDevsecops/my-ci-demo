pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/PratikshaDevsecops/my-ci-demo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Syntax Check') {
            steps {
                // This will fail if Python file has syntax errors
                sh 'python -m py_compile app.py'
            }
        }

        stage('Build') {
            steps {
                echo "Build successful! No syntax errors detected."
            }
        }
    }

    post {
        failure {
            echo "❌ Build failed due to a human error in code!"
        }
        success {
            echo "✅ Build passed!"
        }
    }
}