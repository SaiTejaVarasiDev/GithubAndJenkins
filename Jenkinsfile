// pipeline {
//     agent any
//     environment{
//         SF_INSTANCE_URL = credentials('SF_INSTANCE_URL')
//         SF_USERNAME = credentials('SF_USERNAME')
//         SF_CONSUMER_KEY = credentials('SF_CONSUMER_KEY')
//         SF_SERVER_KEY = credentials('SF_SERVER_KEY')
//         // def toolbelt = tool 'salesforce'
        
//     }
//     stages {
//         stage('stage1') {
//             steps {
//                 echo "Running stage 1"
//                 echo "$SF_INSTANCE_URL"
//                 echo "$SF_USERNAME"
//                 echo "$SF_CONSUMER_KEY"
//                 echo "$SF_SERVER_KEY"
//                 // echo "${env.SF_INSTANCE_URL}"
//                 // echo "${env.SF_USERNAME}"
//                 // echo "${env.SF_CONSUMER_KEY}"
//             }
//         }
//         stage('stage2') {
//             steps {
//                 echo "Running stage 2"
//                 withCredentials([file(credentialsId: 'SF_SERVER_KEY', variable: 'secret_file_key')]){
//                     echo "${secret_file_key}"
//                 }
//             }
//         }
//     }
// }

#!groovy

import groovy.json.JsonSlurperClassic

node {
    def SF_INSTANCE_URL = credentials('SF_INSTANCE_URL')
    def SF_USERNAME = credentials('SF_USERNAME')
    def SF_CONSUMER_KEY = credentials('SF_CONSUMER_KEY')

    def toolbelt = tool 'salesforce'

    stage('checkout source') {
        checkout scm
    }

    withEnv(["HOME=${env.WORKSPACE}"]) {

        withCredentials([file(credentialsId: SF_SERVER_KEY, variable: 'server_key_file')]) {
            stage('Authorize DevHub') {
                rc = command "${toolbelt}/sf org login jwt --instance-url ${SF_INSTANCE_URL} --client-id ${SF_CONSUMER_KEY} --username ${SF_USERNAME} --jwt-key-file ${server_key_file} --set-default-dev-hub --alias HubOrg"
                if (rc != 0) {
                    error 'Salesforce dev hub org authorization failed.'
                }
            }
        }
    }
    
}

def command(script) {
    if (isUnix()) {
        return sh(returnStatus: true, script: script);
    } else {
        return bat(returnStatus: true, script: script);
    }
}
