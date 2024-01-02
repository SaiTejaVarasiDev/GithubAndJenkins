pipeline {
    agent any
    environment{
        SF_INSTANCE_URL = credentials('SF_INSTANCE_URL')
        SF_USERNAME = credentials('SF_USERNAME')
        SF_CONSUMER_KEY = credentials('SF_CONSUMER_KEY')
        SF_SERVER_KEY = credentials('SF_SERVER_KEY')
        // toolbelt = tool name: 'salesforce_cli'
        // sf_path = "C:/Windows/System32/config/systemprofile/AppData/Local/Jenkins/.jenkins/tools/com.cloudbees.jenkins.plugins.customtools.CustomTool/salesforce/sf/bin"
        
        
        
    }
    parameters {
        string(name: 'apexclass_path', defaultValue: 'C:/Windows/System32/config/systemprofile/AppData/Local/Jenkins/.jenkins/workspace/p1 pipeline', description: 'path')
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
        stage('Checking Server key access') {
            steps {
                echo "Running stage 2"
                withCredentials([file(credentialsId: 'SF_SERVER_KEY', variable: 'secret_file_key')]){
                    echo "${secret_file_key}"
                }
            }
        }
        stage('check plugin') {
            steps {
                echo "PATH: ${env.PATH}"
                bat "dir"
                bat "sf --version"
            }
        }
        
        // stage('Authenticate with Salesforce') {
        //     steps {
        //         echo "PATH: ${env.PATH}"
        //         withEnv(["PATH+EXTRA=$sf_path"]) {
        //             bat "sf --version"
        //         }
                
        //     }
        // }
        // stage('Authorize To ORG and deploy testing') {
        //     steps {
        //         withEnv(["HOME=${env.WORKSPACE}"]) {
        //             dir('C:/Windows/System32/config/systemprofile/AppData/Local/Jenkins/.jenkins/tools/com.cloudbees.jenkins.plugins.customtools.CustomTool/salesforce/sf/bin'){
        //                 withCredentials([file(credentialsId: 'SF_SERVER_KEY', variable: 'secret_file_key')]){
        //                     // echo "${secret_file_key}"
        //                     bat "sf org login jwt --instance-url ${SF_INSTANCE_URL} --client-id ${SF_CONSUMER_KEY} --username ${SF_USERNAME} --jwt-key-file ${secret_file_key} --set-default-dev-hub --alias HubOrg"
        //                     bat "sf deploy metadata preview -d ${params.apexclass_path}"
                            
        //                 }
        //             }
        //         }
        //     }
        // }
        
    }
}







