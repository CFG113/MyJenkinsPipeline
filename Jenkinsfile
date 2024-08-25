pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                // Example build step: sh 'mvn clean package'
                echo 'Tool used: Maven'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests to ensure code functions as expected...'
                echo 'Running integration tests to ensure components work together...'
                // Example test step: sh 'mvn test'
                echo 'Tools used: JUnit for unit tests, Selenium for integration tests'
            }
            post {
                always {
                    script {
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
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis to ensure code meets industry standards...'
                // Example analysis step: sh 'sonar-scanner'
                echo 'Tool used: SonarQube'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan to identify vulnerabilities in the code...'
                // Example security scan step: sh 'dependency-check --project MyProject --scan .'
                echo 'Tool used: OWASP Dependency Check'
            }
            post {
                always {
                    script {
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
                echo 'Deploying the application to the staging server...'
                // Example deploy step: sh 'scp target/myapp.war user@staging-server:/path/to/deploy'
                echo 'Tool used: AWS CLI for deployment to AWS EC2 instance'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment...'
                // Example integration tests on staging: sh 'mvn verify -DtestEnv=staging'
                echo 'Tools used: JUnit and Selenium for integration tests on staging'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to the production server...'
                // Example deploy to production step: sh 'scp target/myapp.war user@production-server:/path/to/deploy'
                echo 'Tool used: AWS CLI for deployment to AWS EC2 instance'
            }
        }
    }
}
