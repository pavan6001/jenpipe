pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running Test server deployment'
            }
        }
        stage('DeployToTest') {
           
            steps {
                withCredentials([usernamePassword(credentialsId: 'ubuntu_server_pvtkey', usernameVariable: 'USERNAME', passwordVariable: 'USERPASS')]) {
                    sshPublisher(
                        failOnError: true,
                        continueOnError: false,
                        publishers: [
                            sshPublisherDesc(
                                configName: 'Testserver',
                                sshCredentials: [
                                    username: "$USERNAME",
                                    encryptedPassphrase: "$USERPASS"
                                ], 
                                transfers: [
                                    sshTransfer(
                                        sourceFiles: 'index.php',
                                        remoteDirectory: '/var/www/html/',
                                        execCommand: 'sudo /usr/bin/systemctl stop httpd && sudo /usr/bin/systemctl start httpd'
                                    )
                                ]
                            )
                        ]
                    )
                }
            }
        }
	}
}
