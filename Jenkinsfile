pipeline {
    agent any
    environment {
        GIT_REPO_URL = 'https://github.com/npestov9/IT-6.1C'
        STAGING_ENVIRONMENT = 'staging-server'
        PRODUCTION_ENVIRONMENT = 'production-server'
        RECIPIENT_EMAIL = 'npestov9@gmail.com'
    }
    stages {
        stage('Deploy to Staging') {
            steps {
                script {
                    echo "Deploying to staging server: ${env.STAGING_ENVIRONMENT}"
                }
            }
            post {
                always {
                    script {
                        echo "Workspace path: ${env.WORKSPACE}"
                        echo "Expected log path: ${env.WORKSPACE}/../${env.JOB_NAME}/builds/${env.BUILD_ID}/log"

                        // Attempt to capture the full log
                        def fullLog = sh(script: "cat ${env.WORKSPACE}/../${env.JOB_NAME}/builds/${env.BUILD_ID}/log || echo 'Log file not found'", returnStdout: true).trim()

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
        // Similar setup for Deploy to Production stage
    }
}
