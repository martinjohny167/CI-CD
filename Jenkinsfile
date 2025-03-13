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
                // Verify Python is available and install dependencies
                sh 'python3 --version'
                sh 'pip3 install --user -r requirements.txt'
            }
        }
        stage('Build') {
            steps {
                // Simulate a build process (Flask apps don’t require compilation)
                sh 'echo "Building the application..."'
            }
        }
        stage('Test') {
            steps {
                // Run the unit tests
                sh 'pytest test_app.py'
            }
        }
        stage('Deploy') {
            steps {
                // Simulate deployment (optional per lab requirements)
                sh 'echo "Deploying to cloud provider..."'
            }
        }
    }
    post {
        always {
            // Send email notification with build status
            mail to: 'your-college-email@college.edu',
                 subject: "Jenkins Build ${currentBuild.fullDisplayName} - ${currentBuild.result}",
                 body: "Build status: ${currentBuild.result}\nCheck Jenkins console output at ${env.BUILD_URL}"
        }
    }
}
