pipeline {
    agent any
    stages {
        stage('stage1') {
            steps {
                echo "Running stage 1"
                echo "${env.SF_INSTANCE_URL}"
                echo "${env.SF_USERNAME}"
                echo "${env.SF_CONSUMER_KEY}"
            }
        }
        stage('stage2') {
            steps {
                echo "Running stage 2"
            }
        }
    }
}
