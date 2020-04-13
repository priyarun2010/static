pipeline {
agent any 
    stages {
        stage('Lint HTML') {
            steps {
                sh 'tidy -q -e *.html'
            }
        }
        stage('Upload to AWS') {
            steps {
                withAWS(credentials: 'aws-static', region: 'us-west-2') {
                    s3Upload (bucket: 'priya-jenkins-s3', file: 'index.html')
                }
            }
        }
    }
}
