pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'rsync -avz C:\Program\ Files\ (x86)\Jenkins\workspace\JenkinsTest ubuntu@15.206.25.72:/var/www/html/'
            }
        }
    }
}
