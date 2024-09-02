pipeline {
    agent any
    environment {
        GIT_REPO_URL = 'https://github.com/npestov9/IT-6.1C'
        STAGING_ENVIRONMENT = 'staging-server'
        PRODUCTION_ENVIRONMENT = 'production-server'
        RECIPIENT_EMAIL = 'npestov9@gmail.com' //comment
    }
    stages {
        stage('Build') {
            steps {
                script {
                    echo "Building the code using Maven"
                }
            }
            post {
                always {
                    script {
                        // Capture Jenkins console log and write it to a file
                        archiveArtifacts artifacts: '**/build.log', allowEmptyArchive: true
                        // Send the email with the Jenkins log attached
                        mail bcc: '',
                             body: "Build stage completed. Status: ${currentBuild.currentResult}",
                             cc: '',
                             from: '',
                             replyTo: '',
                             subject: "Build Stage Status",
                             to: "${env.RECIPIENT_EMAIL}",
                             attachmentsPattern: '**/build.log'
                    }
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
            post {
                always {
                    script {
                        // Capture Jenkins console log and write it to a file
                        archiveArtifacts artifacts: '**/unit_and_integration_tests.log', allowEmptyArchive: true
                        // Send the email with the Jenkins log attached
                        mail bcc: '',
                             body: "Unit and integration tests completed. Status: ${currentBuild.currentResult}",
                             cc: '',
                             from: '',
                             replyTo: '',
                             subject: "Unit and Integration Tests Status",
                             to: "${env.RECIPIENT_EMAIL}",
                             attachmentsPattern: '**/unit_and_integration_tests.log'
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo "Analyzing code quality using SonarQube"
                }
            }
            post {
                always {
                    script {
                        // Capture the log
                        sh 'cat ${WORKSPACE}/log > code_analysis.log'
                        // Send the email with the log attached
                        mail bcc: '',
                             body: "Code analysis completed. Status: ${currentBuild.currentResult}",
                             cc: '',
                             from: '',
                             replyTo: '',
                             subject: "Code Analysis Status",
                             to: "${env.RECIPIENT_EMAIL}",
                             attachmentsPattern: 'code_analysis.log'
                    }
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo "Performing security scan using OWASP ZAP"
                }
            }
            post {
                always {
                    script {
                        // Capture the log
                        sh 'cat ${WORKSPACE}/log > security_scan.log'
                        // Send the email with the log attached
                        mail bcc: '',
                             body: "Security scan completed. Status: ${currentBuild.currentResult}",
                             cc: '',
                             from: '',
                             replyTo: '',
                             subject: "Security Scan Status",
                             to: "${env.RECIPIENT_EMAIL}",
                             attachmentsPattern: 'security_scan.log'
                    }
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
                        // Capture the log
                        sh 'cat ${WORKSPACE}/log > deploy_to_staging.log'
                        // Send the email with the log attached
                        mail bcc: '',
                             body: "Deployment to staging completed. Status: ${currentBuild.currentResult}",
                             cc: '',
                             from: '',
                             replyTo: '',
                             subject: "Deploy to Staging Status",
                             to: "${env.RECIPIENT_EMAIL}",
                             attachmentsPattern: 'deploy_to_staging.log'
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
            post {
                always {
                    script {
                        // Capture the log
                        sh 'cat ${WORKSPACE}/log > integration_tests_on_staging.log'
                        // Send the email with the log attached
                        mail bcc: '',
                             body: "Integration tests on staging completed. Status: ${currentBuild.currentResult}",
                             cc: '',
                             from: '',
                             replyTo: '',
                             subject: "Integration Tests on Staging Status",
                             to: "${env.RECIPIENT_EMAIL}",
                             attachmentsPattern: 'integration_tests_on_staging.log'
                    }
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
                        // Capture the log
                        sh 'cat ${WORKSPACE}/log > deploy_to_production.log'
                        // Send the email with the log attached
                        mail bcc: '',
                             body: "Deployment to production completed. Status: ${currentBuild.currentResult}",
                             cc: '',
                             from: '',
                             replyTo: '',
                             subject: "Deploy to Production Status",
                             to: "${env.RECIPIENT_EMAIL}",
                             attachmentsPattern: 'deploy_to_production.log'
                    }
                }
            }
        }
    }//not up to date
}
