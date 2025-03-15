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
                    bat 'echo Building on Windows'
                    echo 'Build complete'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo 'Running tests...'
                    bat 'echo Running tests on Windows'
                    echo 'Test complete'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying application...'
                    bat 'echo Deploying on Windows'
                    echo 'Application deployed on Windows'
                }
            }
        }
    }

    post {
        always {
            script {
                def buildStatus = currentBuild.currentResult
                def buildUser = currentBuild.getBuildCauses('hudson.model.Cause$UserIdCause')[0]?.userId ?: 'Github User'

                echo "Build Status: ${buildStatus}"
                echo "Started by: ${buildUser}"

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
                    mimeType: 'text/html'
                )
            }
        }

        success {
            script {
                echo 'Build, Test, and Deploy succeeded! Sending success email...'
                emailext(
                    subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER} - Build, Test, and Deploy",
                    body: """
                    <p>The pipeline has completed successfully!</p>
                    <p>Project: ${env.JOB_NAME}</p>
                    <p>Build Number: ${env.BUILD_NUMBER}</p>
                    <p>Build Status: SUCCESS</p>
                    <p>Started by: ${currentBuild.getBuildCauses('hudson.model.Cause$UserIdCause')[0]?.userId}</p>
                    <p>Build URL: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                    """,
                    to: 'martinjohny29@gmail.com',
                    from: 'martinjohny29@gmail.com',
                    replyTo: 'mjohny5124@conestogac.on.ca',
                    mimeType: 'text/html'
                )
            }
        }

        failure {
            script {
                echo 'Build failed! Sending failure email...'
                emailext(
                    subject: "FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER} - Build or Deploy Failed",
                    body: """
                    <p>The pipeline has failed!</p>
                    <p>Project: ${env.JOB_NAME}</p>
                    <p>Build Number: ${env.BUILD_NUMBER}</p>
                    <p>Build Status: FAILURE</p>
                    <p>Started by: ${currentBuild.getBuildCauses('hudson.model.Cause$UserIdCause')[0]?.userId}</p>
                    <p>Build URL: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                    """,
                    to: 'martinjohny29@gmail.com',
                    from: 'martinjohny29@gmail.com',
                    replyTo: 'mjohny5124@conestogac.on.ca',
                    mimeType: 'text/html'
                )
            }
        }

        unstable {
            script {
                echo 'Pipeline is unstable! Sending email...'
                emailext(
                    subject: "UNSTABLE: ${env.JOB_NAME} #${env.BUILD_NUMBER} - Build Unstable",
                    body: """
                    <p>The pipeline has finished with an unstable result.</p>
                    <p>Project: ${env.JOB_NAME}</p>
                    <p>Build Number: ${env.BUILD_NUMBER}</p>
                    <p>Build Status: UNSTABLE</p>
                    <p>Started by: ${currentBuild.getBuildCauses('hudson.model.Cause$UserIdCause')[0]?.userId}</p>
                    <p>Build URL: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                    """,
                    to: 'martinjohny29@gmail.com',
                    from: 'martinjohny29@gmail.com',
                    replyTo: 'mjohny5124@conestogac.on.ca',
                    mimeType: 'text/html'
                )
            }
        }
    }
}
