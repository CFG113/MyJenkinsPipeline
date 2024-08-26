pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                // Example build step: sh 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests and integration tests...'
                echo 'Tools used: JUnit for unit tests, Selenium for integration tests'
                // Example test step: sh 'mvn test'
            }
            post {
                always {
                    script {
                        echo "Sending email for Unit and Integration Tests stage"
                        def status = currentBuild.currentResult
                        emailext (
                            subject: "Jenkins: Unit and Integration Tests Stage Result - ${status}",
                            body: """<p>The 'Unit and Integration Tests' stage has finished with status: <strong>${status}</strong>.</p>""",
                            to: 'christianghantous1@gmail.com',
                            mimeType: 'text/html',
                            attachLog: true
                        )
                    }
                }
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Running security scan to identify vulnerabilities...'
                // Example security scan step: sh 'security-scan-command'
            }
            post {
                always {
                    script {
                        echo "Sending email for Security Scan stage"
                        def status = currentBuild.currentResult
                        emailext (
                            subject: "Jenkins: Security Scan Stage Result - ${status}",
                            body: """<p>The 'Security Scan' stage has finished with status: <strong>${status}</strong>.</p>""",
                            to: 'christianghantous1@gmail.com',
                            mimeType: 'text/html',
                            attachLog: true
                        )
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to the staging server using AWS CLI...'
                // Example deploy step: sh 'scp target/myapp.war user@staging-server:/path/to/deploy'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment using JUnit and Selenium...'
                // Example integration tests on staging: sh 'mvn verify -DtestEnv=staging'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to the production server using AWS CLI..'
                // Example deploy to production step: sh 'scp target/myapp.war user@production-server:/path/to/deploy'
            }
        }
    }
}
