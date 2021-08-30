pipeline {
  agent any
  triggers {
      cron('0 0,12 * * *')
      }
  stages {  
    stage('SSH to host & Backup Postgress') {
      steps {
        script {
          withCredentials([string(credentialsId: 'sshHostPassSecret', variable: 'pass')]) {
            sh"""
            sshpass -p $pass ssh root@188.166.87.169
            echo "Login to Host successfull"
            docker exec -t realworld_postgres pg_dumpall -c -U user > postgres_dump.sql
            mv ./postgres_dump.sql /var/jenkins_home/postgressBackup/postgres_dump-${env.BUILD_NUMBER}.sql
            """
            }
          }
        }
      }
    }
  }

