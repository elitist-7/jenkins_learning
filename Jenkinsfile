pipeline {
    agent any

    environment {
        MY_NAME = "ayanokoji"
        // my_credentials = credentials("3318c43a-1562-4e58-80c2-224631c832f0")
    }

    parameters {
        string(name: 'VERSION', defaultValue: '', description: "Version to deploy for prod")
        choice(name: 'Services', choices: ['frontend', 'backend'], description: "Service to deploy")
        booleanParam(name: 'Execute_Tests', defaultValue: true, description: '')
    }

    stages {
        stage("Build") {
            steps {
                echo "using the branch name ${BRANCH_NAME}"
                withCredentials([
                    usernamePassword(credentialsId: "3318c43a-1562-4e58-80c2-224631c832f0", usernameVariable: USER, passwordVariable: PWD)
                    ]) {
                    echo "user is: ${USER}, and password is ${PWD}"
                }
                echo "Starting the build"
            }
        }
        stage("Test") {
            when {
                expression {
                    params.Execute_Tests == true
                }
            }

            steps {
                echo "Testing the build"
            }
        }
        stage("Deploy") {
            steps {
                echo "Deploying the build, version: ${params.VERSION}"
                echo "Successfully deployed ,${MY_NAME}"
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
