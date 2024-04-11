steps {
    sshagent(credentials: ['ssh-credentials-id']) {
      sh '''
          [ -d ~/.ssh ] || mkdir ~/.ssh && chmod 0700 ~/.ssh
          ssh-keyscan -t rsa,dsa sanityuser86 >> ~/.ssh/known_hosts
          ssh sanityuser86 ...
      '''
    }
}
