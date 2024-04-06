pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                echo "Starting the build"
            }
        }
        stage("Test") {
            steps {
                echo "Testing the build"
            }
        }
        stage("Deploy") {
            steps {
                echo "Deploying the build"
            }
        }
    }

    post {
        always {
            echo "Mandatory- after build"
        }
        success {
            echo "Deployed successfully and no errors found"
        }
        failure {
            echo "Pipeline failed cannot be deployed"
        }
    }
}
