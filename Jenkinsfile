pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }      
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-east-2',credentials:'credsforwebapps3') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'myportfoliowebapp')
                       s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'css', bucket:'myportfoliowebapp')
                       s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'js', bucket:'myportfoliowebapp')
                       s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'assets', bucket:'myportfoliowebapp')
                  }
              }
         }
     }
}
