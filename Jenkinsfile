pipeline {
  agent any 
  stages {
    stage ('Build') {
      steps {
        echo 'Running Test server deployment'
        }
      }
    stage ('DeploytoTest') {
      when {
        branch 'master'
      }
      steps {
        withCredentails([string(credentailsId: 'cloud_user_pw', variable: 'USERPASS')]) {
          sshPublisher(
              failOnError: true,
              publishers: [ 
                  sshPublisherDesc(
                    configName: 'Testserver',
                    sshCredddentials: [
                        username: 'cloud_user',
                        encryptedPassphrase: "$USERPASS"
                      ],
                    transfers: [
                      sshTransfer(
                          sourceFiles: 'index.php',
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
