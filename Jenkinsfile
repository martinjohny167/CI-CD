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
                        bat 'echo Building on Windows'  // Removed extra space
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
                        bat 'echo Running tests on Windows'  // Removed extra space
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
                        bat 'echo Deploying on Windows'  // Removed extra space
                    }
                }
            }
        }
    }

    post {
        always {
            script {
                def buildStatus = currentBuild.currentResult
                def buildUser = currentBuild.getBuildCauses('hudson.model.Cause$UserIdCause')[0]?.userId ?: 'Github User'

                emailext(
                    subject: "Pipeline ${buildStatus}: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                    body: """
                    <p>This is a Jenkins BINGO CICD pipeline status.</p>
                    <p>Project: ${env.JOB_NAME}</p>
                    <p>Build Number: ${env.BUILD_NUMBER}</p>
                    <p>Build Status: ${buildStatus}</p>
                    <p>Started by: ${buildUser}</p>
                    <p>Build URL: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                    """,
                    to: 'martinjohny29@gmail.com',
                    from: 'martinjohny29@gmail.com',
                    replyTo: 'mjohny5124@conestogac.on.ca',
                    mimeType: 'text/html',
                    attachmentsPattern: 'trivyfs.txt,trivyimage.txt'
                )
            }
        }
    }
}
