node {
   def commit_id
   stage('Preparation') {
     checkout scm
     sh "git rev-parse --short HEAD > .git/commit-id"                        
     commit_id = readFile('.git/commit-id').trim()
   }
  
   stage('SSH to host') {
    withCredentials([usernamePassword(credentialsId: 'sshToHost', passwordVariable: 'pass', usernameVariable: 'user')]) {
       sh"""
       ssh -p $pass ssh root@188.166.87.169
       echo "Login to Host successfull"
       whoami
       """
    }
  }
}

