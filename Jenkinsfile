pipeline {
    agent any
    stages {
        stage('stage1') {
            steps {
                echo "Running stage 1"
                def SF_CONSUMER_KEY = env.SF_CONSUMER_KEY
                def SF_USERNAME = env.SF_USERNAME
                def SF_INSTANCE_URL = env.SF_INSTANCE_URL
                echo ${SF_INSTANCE_URL}
                echo ${SF_USERNAME}
                echo ${SF_CONSUMER_KEY}
            }
        }
        stage('stage2') {
            steps {
                echo "Running stage 2"
            }
        }
    }
}
