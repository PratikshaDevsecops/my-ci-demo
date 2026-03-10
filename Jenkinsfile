pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                // Explicitly checkout main branch
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
                // Fail if Python file has syntax errors
                sh 'python -m py_compile app.py'
            }
        }

        stage('Run App') {
            steps {
                // Run the Python script and print output
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