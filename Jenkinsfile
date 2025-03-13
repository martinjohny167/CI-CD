
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the main branch
                git branch: 'main', credentialsId: 'github-pat-for-ci-cd', url: 'https://github.com/martinjohny167/CI-CD.git'
            }
        }
        stage('Tool Setup') {
            steps {
                // Use bat for Windows commands
                bat 'python --version'
                bat 'pip install -r requirements.txt'
            }
        }
        stage('Build') {
            steps {
                // Simulate build process
                bat 'echo "Building the application..."'
            }
        }
        stage('Test') {
            steps {
                // Run tests with pytest
                bat 'pytest test_app.py'
            }
        }
        stage('Deploy') {
            steps {
                // Simulate deployment (optional)
                bat 'echo "Deploying to cloud provider..."'
            }
        }
    }
   
}
