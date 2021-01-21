node {

    checkout scm

 def img = stage('Build') {
          docker.build("test",  '.')
    }
    stage('Run') {
            img.withRun("--name run-$BUILD_ID -p 8081:8080") { c ->
            bat 'docker ps'
            bat 'netstat -ntaup'
            bat 'sleep 30s'
            bat 'curl 127.0.0.1:8081'
            bat 'docker ps'
          }
    }

}
