pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                script {
                    echo 'Cloning repository...'
                    checkout scm 
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    echo 'Simulating build process...'
                    if (isUnix()) {
                        sh 'echo "Building on Unix/Linux"'
                    } else {
                        bat 'echo Building on Windows'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo 'Running tests...'
                    if (isUnix()) {
                        sh 'echo "Running tests on Unix/Linux"'
                    } else {
                        bat 'echo Running tests on Windows'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying application...'
                    if (isUnix()) {
                        sh 'echo "Deploying on Unix/Linux"'
                    } else {
                        bat 'echo Deploying on Windows'
                    }
                }
            }
        }
    }

    post {
        success {
            script {
                echo 'Pipeline successfully completed!'
                // Send success email notification
                emailext(
                    subject: "Jenkins Build Success: ${currentBuild.fullDisplayName}",
                    body: "The pipeline was successfully completed.",
                    to: 'Mjohny5124@conestogac.on.ca'
                )
            }
        }

        failure {
            script {
                echo 'Pipeline failed!'
                // Send failure email notification
                emailext(
                    subject: "Jenkins Build Failure: ${currentBuild.fullDisplayName}",
                    body: "The pipeline failed. Please check the build logs.",
                    to: 'Mjohny5124@conestogac.on.ca'
                )
            }
        }

        always {
            script {
                echo 'Cleaning up...'
                // You can add any cleanup tasks here if needed
            }
        }
    }
}
