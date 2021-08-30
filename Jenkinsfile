node {
   def commit_id
   stage('Preparation') {
     checkout scm
     sh "git rev-parse --short HEAD > .git/commit-id"                        
     commit_id = readFile('.git/commit-id').trim()
   }
  
   stage('SSH to host & Backup Postgress') {
    withCredentials([string(credentialsId: 'sshHostPassSecret', variable: 'pass')]) {
       sh"""
       sshpass -p $pass ssh root@188.166.87.169
       echo "Login to Host successfull"
       docker exec -t realworld_postgres pg_dumpall -c -U user > postgres_dump.sql
       mv ./postgres_dump.sql /root/demoApp/postgress/backup/postgres_dump-${commit_id}-${env.BUILD_NUMBER}.sql
       """
    }
  }
}

