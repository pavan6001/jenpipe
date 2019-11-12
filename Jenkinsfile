pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running Test server deployment'
            }
        }
        stage('DeployToTest') {
		environment {
			SSH_CREDS = credentials('ubuntu_server_pvtkey')
			}
            steps {
		sh 'echo "SSH private key is located at $SSH_CREDS"'
                sh 'echo "SSH user is $SSH_CREDS_USR"'
                sh 'echo "SSH passphrase is $SSH_CREDS_PSW"'
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
