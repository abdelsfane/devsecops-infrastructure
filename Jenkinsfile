#!/usr/bin/env groovy

node {
  checkout scm

// ------------------------------- Define Variables ------------------------------------------------
  APPLICATION_NAME = "AbdelSpringMusic"
  PCF_ENDPOINT = "https://api.run.pivotal.io"
  NEXPOSE_ENDPOINT = "https://18.222.122.198"
  EXCEPTIONS_LIST_URL = "https://gist.github.com/abdelsfane/9dab45201be6f8e7a942a27ac48ffaf1"
  ASSET_IP = "3.17.145.188"
  SITE_NAME = "$ASSET_IP_$BUILD_NUMBER"


// ------------------------------- Use Jenkins Credential Store ------------------------------------------------

  withCredentials([
        [
        $class          : 'UsernamePasswordMultiBinding',
        credentialsId   : 'NEXPOSE_CREDS',
        passwordVariable: 'PASSWORD',
        usernameVariable: 'USERNAME'
        ]]){

// ------------------------------- Spin Up Docker Container ------------------------------------------------

    stage("Run Nexpose Scan") {
      sh '''
        scan --connection $NEXPOSE_ENDPOINT --exceptions_list_url $EXCEPTIONS_LIST_URL --username $USERNAME --password $PASSWORD --port 443 --site-name $SITE_NAME --ip-addresses $ASSET_IP --scan-template full-audit
        '''
    }
      stage("Cleaning Worksapce") {
        cleanWs()
      }
     }
   }