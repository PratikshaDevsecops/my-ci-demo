pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/PratikshaDevsecops/my-ci-demo.git'
            }
        }

        stage('Setup Python Environment') {
            steps {
                // Create a virtual environment
                sh 'python3 -m venv venv'
                
                // Activate venv and upgrade pip
                sh '. venv/bin/activate && pip install --upgrade pip'
                
                // Install requirements inside venv
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Syntax Check') {
            steps {
                // Run syntax check inside venv
                sh '. venv/bin/activate && python -m py_compile app.py'
            }
        }

        stage('Run App') {
            steps {
                // Run the Python app inside venv
                sh '. venv/bin/activate && python app.py'
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
            echo "❌ Build failed due to a human error in code or environment!"
        }
        success {
            echo "✅ Build passed successfully!"
        }
    }
}