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
            post {
                always {
                    script {
                        // Send an email with the console log attached
                        emailext subject: "Build Stage Status: ${currentBuild.currentResult}",
                                 body: """Build stage completed. Status: ${currentBuild.currentResult}
                                 You can view the full build log at: ${env.BUILD_URL}console
                                 """,
                                 to: "${env.RECIPIENT_EMAIL}",
                                 attachLog: true
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
                        // Send an email with the console log attached
                        emailext subject: "Unit and Integration Tests Status: ${currentBuild.currentResult}",
                                 body: """Unit and Integration Tests completed. Status: ${currentBuild.currentResult}
                                 You can view the full test log at: ${env.BUILD_URL}console
                                 """,
                                 to: "${env.RECIPIENT_EMAIL}",
                                 attachLog: true
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
                        // Send an email with the console log attached
                        emailext subject: "Code Analysis Status: ${currentBuild.currentResult}",
                                 body: """Code analysis completed. Status: ${currentBuild.currentResult}
                                 You can view the full code analysis log at: ${env.BUILD_URL}console
                                 """,
                                 to: "${env.RECIPIENT_EMAIL}",
                                 attachLog: true
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
                        // Send an email with the console log attached
                        emailext subject: "Security Scan Status: ${currentBuild.currentResult}",
                                 body: """Security scan completed. Status: ${currentBuild.currentResult}
                                 You can view the full security scan log at: ${env.BUILD_URL}console
                                 """,
                                 to: "${env.RECIPIENT_EMAIL}",
                                 attachLog: true
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
                        // Send an email with the console log attached
                        emailext subject: "Deploy to Staging Status: ${currentBuild.currentResult}",
                                 body: """Deployment to staging completed. Status: ${currentBuild.currentResult}
                                 You can view the full deployment log at: ${env.BUILD_URL}console
                                 """,
                                 to: "${env.RECIPIENT_EMAIL}",
                                 attachLog: true
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
                        // Send an email with the console log attached
                        emailext subject: "Integration Tests on Staging Status: ${currentBuild.currentResult}",
                                 body: """Integration tests on staging completed. Status: ${currentBuild.currentResult}
                                 You can view the full integration test log at: ${env.BUILD_URL}console
                                 """,
                                 to: "${env.RECIPIENT_EMAIL}",
                                 attachLog: true
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
                        // Send an email with the console log attached
                        emailext subject: "Deploy to Production Status: ${currentBuild.currentResult}",
                                 body: """Deployment to production completed. Status: ${currentBuild.currentResult}
                                 You can view the full production deployment log at: ${env.BUILD_URL}console
                                 """,
                                 to: "${env.RECIPIENT_EMAIL}",
                                 attachLog: true
                    }
                }
            }
        }
    }
}
