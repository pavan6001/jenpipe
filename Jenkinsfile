pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'rsync -avz /var/lib/jenkins/jobs/JenkinsTest/* ubuntu@15.206.25.72:/var/www/html/'
            }
        }
    }
}
