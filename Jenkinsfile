pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: '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', url: 'https://github.com/martinjohny167/CI-CD'
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
