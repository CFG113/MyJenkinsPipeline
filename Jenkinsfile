pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                echo 'Tool used: Maven'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests to ensure code functions as expected...'
                echo 'Running integration tests to ensure components work together...'
                echo 'Tools used: JUnit for unit tests, Selenium for integration tests'
            }
            post {
                always {
                    script {
                        echo "About to send email for Unit and Integration Tests stage"
                        def status = currentBuild.currentResult
                        emailext (
                            subject: "Jenkins: Test Stage Result - ${status}",
                            body: """<p>The 'Unit and Integration Tests' stage has finished with status: <strong>${status}</strong>.</p>""",
                            to: 'christianghantous1@gmail.com',
                            mimeType: 'text/html',
                            attachLog: true
                        )
                        echo "Email sent for Unit and Integration Tests stage"
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
