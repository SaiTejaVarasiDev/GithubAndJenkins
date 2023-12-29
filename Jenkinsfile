pipeline {
    agent any
    environment{
        SF_INSTANCE_URL = credentials('SF_INSTANCE_URL')
        SF_USERNAME = credentials('SF_USERNAME')
        SF_CONSUMER_KEY = credentials('SF_CONSUMER_KEY')
        SF_SERVER_KEY = credentials('SF_SERVER_KEY')
        def toolbelt = tool 'salesforce'
        
        
    }
    stages {
        stage('Testing credentials') {
            steps {
                echo "Running stage 1"
                echo "$SF_INSTANCE_URL"
                echo "$SF_USERNAME"
                echo "$SF_CONSUMER_KEY"
                echo "$SF_SERVER_KEY"
                // echo "${env.SF_INSTANCE_URL}"
                // echo "${env.SF_USERNAME}"
                // echo "${env.SF_CONSUMER_KEY}"
            }
        }
        stage('Checking Server key') {
            steps {
                echo "Running stage 2"
                withCredentials([file(credentialsId: 'SF_SERVER_KEY', variable: 'secret_file_key')]){
                    echo "${secret_file_key}"
                }
            }
        }
        stage('Authorize To ORG') {
            steps {
                withEnv(["HOME=${env.WORKSPACE}"]) {
                    echo "Testing sfdx installation"
                    dir('/sf/bin'){
                        withCredentials([file(credentialsId: 'SF_SERVER_KEY', variable: 'secret_file_key')]){
                            echo "${secret_file_key}"
                            bat "sf org login jwt --instance-url ${SF_INSTANCE_URL} --client-id ${SF_CONSUMER_KEY} --username ${SF_USERNAME} --jwt-key-file ${secret_file_key} --set-default-dev-hub --alias HubOrg"
                        }
                    }
                }
            }
        }
    }
}







