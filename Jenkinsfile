pipeline {
    agent any
    environment {
        DIRECTORY_PATH = "/dummy/path"
        TESTING_ENVIRONMENT = "MyFirstTestingEnvironment"
        PRODUCTION_ENVIRONMENT = "MyFirstProductionEnvironment "
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                echo 'Using Maven...'
            }
            post {
                success {
                    echo 'Build successful!'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JUnit...'
                echo 'Running integration tests with Cucumber...'
            }
            post {
              success {
                mail to: 'andrew.cho1992@gmail.com',
                subject: 'Build Successful',
                body: 'Build Successful'
              }
              failure {
                mail to: 'andrew.cho1992@gmail.com',
                subject: 'Build Failed',
                body: 'Build Failed'
              }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Running code analysis with Checkov...'
            }
            post {
                success {
                    echo 'Code Analysis successful!'
                }
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Scanning for security issues with Spotbugs...'
            }
            post {
              success {
                mail to: 'andrew.cho1992@gmail.com',
                subject: 'Security Scan Successful',
                body: 'Security Scan Successful'
              }
              failure {
                mail to: 'andrew.cho1992@gmail.com',
                subject: 'Security Scan Failed',
                body: 'Security Scan Failed'
              }
            }
        }
        stage('Deploy To Staging') {
            steps {
                echo 'Deploying to ECS instance on staging environment...'
                timeout(time: 15, unit: 'SECONDS') {
                    sleep 10
                }
            }
            post {
                success {
                    echo 'Deployment to staging server successful!'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on AWS ECS Staging environment with LocalStack...'
            }
            post {
                success {
                    echo 'Integration tests on AWS ECS Staging environment successful!'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to AWS ECS Production environment...'
            }
            post {
                success {
                    echo 'Deploy to production successful!'
                }
            }
        }
    }
}
