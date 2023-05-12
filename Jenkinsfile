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
                node ('email') { 
                    emailext body: 'Build Successful',
                    subject: 'Build Successful',
                    to: 'andrew.cho1992@gmail.com',
                    attachLog: true
              }
//               failure {
//                 emailext body: 'Build Failure',
//                 subject: 'Build Failure',
//                 to: 'andrew.cho1992@gmail.com',
//                 attachLog: true
//               }
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
//             post {
//               success {
//                 emailext body: 'Security Scan Successful',
//                 subject: 'Security Scan Successful',
//                 to: 'andrew.cho1992@gmail.com',
//                 attachLog: true
//               }
//               failure {
//                 emailext body: 'Security Scan Failure',
//                 subject: 'Security Scan Failure',
//                 to: 'andrew.cho1992@gmail.com',
//                 attachLog: true
//               }
//             }
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
