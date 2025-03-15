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
        failure {
            script {
                echo 'Pipeline failed!'
            }
        }
    }
}
