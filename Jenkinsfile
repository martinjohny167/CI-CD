pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/martinjohny167/CI-CD.git'
        BRANCH_NAME = 'main'
        CREDENTIALS_ID = 'github-pat-for-ci-cd'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    echo 'Cloning repository...'
                    checkout([
                        $class: 'GitSCM', 
                        branches: [[name: BRANCH_NAME]], 
                        userRemoteConfigs: [[url: REPO_URL, credentialsId: CREDENTIALS_ID]]
                    ])
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    echo 'Simulating build process...'
                    sh 'echo "Build successful!"'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo 'Running tests...'
                    sh 'echo "All tests passed!"'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo 'Simulating deployment...'
                    sh 'echo "Deployment complete!"'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
            emailext subject: "Jenkins Build Success - ${env.JOB_NAME}",
                     body: "Build ${env.BUILD_NUMBER} completed successfully. View details: ${env.BUILD_URL}",
                     to: 'your-college-email@example.com'
        }

        failure {
            echo 'Pipeline failed!'
            emailext subject: "Jenkins Build Failed - ${env.JOB_NAME}",
                     body: "Build ${env.BUILD_NUMBER} failed. Check logs: ${env.BUILD_URL}",
                     to: 'your-college-email@example.com'
        }
    }
}
