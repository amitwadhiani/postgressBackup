node {
   def commit_id
   stage('Preparation') {
     checkout scm
     sh "git rev-parse --short HEAD > .git/commit-id"                        
     commit_id = readFile('.git/commit-id').trim()
   }
  
   stage('SSH to host') {
    withCredentials([sshUserPrivateKey(credentialsId: 'privateKeyHost', keyFileVariable: 'key', passphraseVariable: 'passphrase', usernameVariable: 'user')]) {
       sh"""
       ssh -p $pass  ssh -p 22 root@188.166.87.169
       echo "Login to Host successfull"
       whoami
       """
    }
  }
}

