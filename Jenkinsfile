pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 bat 'echo "Hello World"'
                 bat '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }      
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-west-2',credentials:'wach-jenkins-cred') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'app.py', bucket:'jenkinupload')
                  }
              }
         }
     }
}
