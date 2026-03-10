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
                // Use pip3 since Python3 is installed inside container
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Syntax Check') {
            steps {
                // Fail if Python file has syntax errors
                sh 'python3 -m py_compile app.py'
            }
        }

        stage('Run App') {
            steps {
                // Run the Python script and print output
                sh 'python3 app.py'
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