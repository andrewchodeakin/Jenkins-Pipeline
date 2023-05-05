pipeline {
    agent any
    environment {
        DIRECTORY_PATH = "/dummy/path"
        TESTING_ENVIRONMENT = "MyFirstTestingEnvironment"
        PRODUCTION_ENVIRONMENT = "MyFirstProductionEnvironment"
    }
    stages {
        stage('Build') {
            steps {
                echo 'fetch the source code from the directory path specified by the environment variable'
                echo 'compile the code and generate any necessary artifacts'
            }
            post {
              success {
                mail to: 'andrew.cho1992@gmail.com',
                subject: 'email sent',
                body: 'email body'
              }
            }
        }
        stage('Test') {
            steps {
                echo 'unit tests'
                echo 'integration tests'
            }
        }
        stage('Code Quality Check') {
            steps {
                echo 'check the quality of the code'
            }
        }
        stage('Deploy') {
            steps {
                echo 'deploy the application to a testing environment specified by the environment variable'
            }
        }
        stage('Approval') {
            steps {
                timeout(time: 15, unit: 'SECONDS') {
                    sleep 10
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "deploy code to $PRODUCTION_ENVIRONMENT"
            }
        }
    }
}
