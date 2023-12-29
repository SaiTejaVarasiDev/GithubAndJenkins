pipeline {
    agent any
    environment{
        SF_INSTANCE_URL = credentials('SF_INSTANCE_URL')
        SF_USERNAME = credentials('SF_USERNAME')
        SF_CONSUMER_KEY = credentials('SF_CONSUMER_KEY')
    }
    stages {
        stage('stage1') {
            steps {
                echo "Running stage 1"
                echo "$SF_INSTANCE_URL"
                echo "$SF_USERNAME"
                echo "$SF_CONSUMER_KEY"
                
                // echo "${env.SF_INSTANCE_URL}"
                // echo "${env.SF_USERNAME}"
                // echo "${env.SF_CONSUMER_KEY}"
            }
        }
        stage('stage2') {
            steps {
                echo "Running stage 2"
            }
        }
    }
}
