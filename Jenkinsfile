pipeline {
    agent any
    stages {
        stage('Send Email') {
            steps {
                emailext(
                    subject: "Test Email Subject",
                    body: "This is a test email.",
                    to: 'mjohny5124@conestogac.on.ca',
                    from: 'martinjohny29@gmail.com',
                    replyTo: 'mjohny5124@conestogac.on.ca',
                    mimeType: 'text/html'
                )
            }
        }
    }
}
