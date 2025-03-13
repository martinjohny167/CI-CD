pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'your-credential-id', url: 'https://github.com/your-repo.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying to cloud...'
            }
        }
    }
    post {
        always {
            mail to: 'your-email@example.com',
                 subject: "Jenkins Build ${currentBuild.result}",
                 body: "Build status: ${currentBuild.result}\nCheck Jenkins console output at ${env.BUILD_URL}"
        }
    }
}
