    stage('SSH commands') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'my-ssh-credentials-id', keyFileVariable: 'MY_SSH_KEY')]) {
                    sh '''
                    ssh -i $MY_SSH_KEY SHA256:bDAyGoEFa/l35X7XKjdtF2UyM7MbP4mYQCQnLuDhatk  "commands to execute"
                    '''
                }
            }
        }
