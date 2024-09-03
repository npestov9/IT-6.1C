pipeline {
    agent any
    environment {
        GIT_REPO_URL = 'https://github.com/npestov9/IT-6.1C'
        STAGING_ENVIRONMENT = 'staging-server'
        PRODUCTION_ENVIRONMENT = 'production-server'
        RECIPIENT_EMAIL = 'npestov9@gmail.com'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    echo "Building the code using Maven"
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo "Running unit tests using JUnit"
                    echo "Running integration tests using Selenium"
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo "Analyzing code quality using SonarQube"
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo "Performing security scan using OWASP ZAP"
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    echo "Deploying to staging server: ${env.STAGING_ENVIRONMENT}"
                }
            }
            post {
                always {
                    script {
                        // Capture the entire Jenkins log
                        def fullLog = sh(script: "cat ${env.WORKSPACE}/../${env.JOB_NAME}/builds/${env.BUILD_ID}/log", returnStdout: true).trim()
                        // Send email after deploying to staging
                        mail bcc: '',
                             body: """Deployment to Staging completed. Status: ${currentBuild.currentResult}

                             Full build log:

                             ${fullLog}

                             """,
                             cc: '',
                             from: '',
                             replyTo: '',
                             subject: "Deploy to Staging Status: ${currentBuild.currentResult}",
                             to: "${env.RECIPIENT_EMAIL}"
                    }
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo "Running integration tests on staging environment"
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo "Deploying to production server: ${env.PRODUCTION_ENVIRONMENT}"
                }
            }
            post {
                always {
                    script {
                        // Capture the entire Jenkins log
                        def fullLog = sh(script: "cat ${env.WORKSPACE}/../${env.JOB_NAME}/builds/${env.BUILD_ID}/log", returnStdout: true).trim()
                        // Send email after deploying to production
                        mail bcc: '',
                             body: """Deployment to Production completed. Status: ${currentBuild.currentResult}

                             Full build log:

                             ${fullLog}

                             """,
                             cc: '',
                             from: '',
                             replyTo: '',
                             subject: "Deploy to Production Status: ${currentBuild.currentResult}",
                             to: "${env.RECIPIENT_EMAIL}"
                    }
                }
            }
        }
    }
}
