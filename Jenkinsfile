#!/usr/bin/env groovy

// Define Variables
def NEXPOSE_ENDPOINT
def EXCEPTIONS_LIST_URL
def ASSET_IP
def SITE_NAME

node {
  checkout scm

// ------------------------------- Set Variables ------------------------------------------------
  NEXPOSE_ENDPOINT = "18.222.122.198"
  EXCEPTIONS_LIST_URL = "https://gist.github.com/abdelsfane/9dab45201be6f8e7a942a27ac48ffaf1"
  ASSET_IP = "3.17.145.188"
  SITE_NAME = "Nexpose_Runner_${BUILD_NUMBER}"


// ------------------------------- Use Jenkins Credential Store ------------------------------------------------

  withCredentials([
        [
        $class          : 'UsernamePasswordMultiBinding',
        credentialsId   : 'NEXPOSE_CREDS',
        passwordVariable: 'PASSWORD',
        usernameVariable: 'USERNAME'
        ]]){

// -------------------------------------------------------------------------------------------------------------

      withEnv(['HOME=.']) {
        env.NEXPOSE_ENDPOINT = NEXPOSE_ENDPOINT
        env.EXCEPTIONS_LIST_URL = EXCEPTIONS_LIST_URL
        env.ASSET_IP = ASSET_IP
        env.SITE_NAME = SITE_NAME

// ------------------------------- Scan Stage ------------------------------------------------------------------

    stage("Run Nexpose Scan") {
      sh '''
        scan --connection ${NEXPOSE_ENDPOINT} --username ${USERNAME} --password ${PASSWORD} --port 3780 --site-name ${SITE_NAME} --ip-addresses ${ASSET_IP} --scan-template full-audit
        '''
    }
      stage("Cleaning Worksapce") {
        cleanWs()
      }
     }
    }
   }