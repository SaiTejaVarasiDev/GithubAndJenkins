pipeline {
    agent any
    environment{
        SF_INSTANCE_URL = credentials('SF_INSTANCE_URL')
        SF_USERNAME = credentials('SF_USERNAME')
        SF_CONSUMER_KEY = credentials('SF_CONSUMER_KEY')
        SF_SERVER_KEY = credentials('SF_SERVER_KEY')
        def toolbelt = tool 'salesforce'
        def command(script) {
            if (isUnix()) {
                return sh(returnStatus: true, script: script);
            } else {
                return bat(returnStatus: true, script: script);
            }
        }
        
    }
    stages {
        stage('stage 1') {
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
        stage('stage no 2') {
            steps {
                echo "Running stage 2"
                withCredentials([file(credentialsId: 'SF_SERVER_KEY', variable: 'secret_file_key')]){
                    echo "${secret_file_key}"
                }
            }
        }
        stage('stage3') {
            steps {
                withEnv(["HOME=${env.WORKSPACE}"]) {
                    echo "Testing sfdx installation"
                    rc = command "${toolbelt}/sf --version"
                    if (rc != 0) {
                        error 'Salesforce dev hub org authorization failed.'
                    }
                }
            }
        }
    }
}





