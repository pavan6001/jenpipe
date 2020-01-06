pipeline {
    agent any
    stages {
        stage('DeployToServer') {
            steps {
                     scp -Cv . cloud_user@15.206.73.254:/var/www/html/
            }
        }
    }
}
