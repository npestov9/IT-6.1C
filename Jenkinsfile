pipeline {
    agent any
    environment {
        GIT_REPO_URL = 'https://github.com/npestov9/IT-6.1C'
        STAGING_ENVIRONMENT = 'staging-server'
        PRODUCTION_ENVIRONMENT = 'production-server'
        RECIPIENT_EMAIL = 'npestov9@gmail.com.com' // Change to your email
    }
    stages {
        stage('Build') {
            steps {
                script {
                    echo "Building the code using Maven"
                    // Example: sh 'mvn clean install'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo "Running unit tests using JUnit"
                    echo "Running integration tests using Selenium"
                    // Example: sh 'mvn test'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo "Analyzing code quality using SonarQube"
                    // Example: sh 'sonar-scanner'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo "Performing security scan using OWASP ZAP"
                    // Example: sh 'zap-baseline.py -t http://example.com'
                }
            }
            post {
                always {
                    emailext subject: "Security Scan Status",
                             body: "Security scan completed. Status: ${currentBuild.currentResult}",
                             to: "${env.RECIPIENT_EMAIL}",
                             attachLog: true
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    echo "Deploying to staging server: ${env.STAGING_ENVIRONMENT}"
                    // Example: sh 'deploy-script.sh staging'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo "Running integration tests on staging environment"
                    // Example: sh 'mvn verify -Pstaging'
                }
            }
            post {
                always {
                    emailext subject: "Integration Tests on Staging Status",
                             body: "Integration tests on staging completed. Status: ${currentBuild.currentResult}",
                             to: "${env.RECIPIENT_EMAIL}",
                             attachLog: true
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo "Deploying to production server: ${env.PRODUCTION_ENVIRONMENT}"
                    // Example: sh 'deploy-script.sh production'
                }
            }
        }
    }
}
