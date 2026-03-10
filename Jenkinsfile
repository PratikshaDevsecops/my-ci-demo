pipeline {
    agent {
        docker {
            image 'python:3.11'  // Python + pip installed
        }
    }

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/PratikshaDevsecops/my-ci-demo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Syntax Check') {
            steps {
                sh 'python -m py_compile app.py'
            }
        }

        stage('Run App') {
            steps {
                sh 'python app.py'
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