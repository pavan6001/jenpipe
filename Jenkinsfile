pipeline {
    agent any
    stages {
        stage('DeployToServer') {
            steps {
                #sh 'rsync -avz /var/lib/jenkins/workspace/jenkinspipe/* ubuntu@15.206.25.72:/var/www/html/'
                scp -Cv . cloud_user@15.206.73.254:/var/www/html/
            }
        }
    }
}
