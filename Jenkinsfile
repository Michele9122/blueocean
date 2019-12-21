pipeline {
  agent any
  stages {
    stage('blueocean') {
      parallel {
        stage('blueocean') {
          steps {
            sleep 1
          }
        }

        stage('aws') {
          steps {
            sh '''pipeline {
    agent any
    stages {
       stage(\'Upload to AWS\') {
             steps {
                 withAWS(region:\'us-east-2\',credentials:\'aws-static\') {
                 sh \'echo "Uploading content with AWS creds"\'
                     s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:\'index.html\', bucket:\'static-jenkins-pipeline\')
                 }
             }
        }
    }
}'''
            }
          }

        }
      }

    }
  }