pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
               bat  'echo "Hello World"'
             }
         }      
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-west-2',credentials:'wach-jenkins-cred') {
                   echo "Uploading content with AWS creds"
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'app.py', bucket:'jenkinupload')
                  }
              }
         }
     }
}
