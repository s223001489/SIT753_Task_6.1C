pipeline {
    agent any

    environment {
        MAVEN_HOME = tool 'Maven'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    sh "${MAVEN_HOME}/bin/mvn clean package"
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests with JUnit
                sh 'mvn test'
                
                // Run integration tests with Selenium
                sh 'mvn verify'
            }
        }

        stage('Code Analysis') {
            steps {
                // Use SonarQube for code analysis
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

        stage('Security Scan') {
            steps {
                // Use OWASP Dependency-Check for security scanning
                sh 'mvn org.owasp:dependency-check-maven:check'
            }
        }

        stage('Deploy to Staging') {
            steps {
                // Use Jenkins SSH Plugin to deploy to staging server
                sshPublisher(
                    publishers: [sshPublisherDesc(
                        configName: 'StagingServer',
                        transfers: [
                            sshTransfer(execCommand: 'deploy.sh')
                        ]
                    )]
                )
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on the staging environment
                sh 'mvn verify -Pstaging'
            }
        }

        stage('Deploy to Production') {
            steps {
                // Use Jenkins SSH Plugin to deploy to production server
                sshPublisher(
                    publishers: [sshPublisherDesc(
                        configName: 'ProductionServer',
                        transfers: [
                            sshTransfer(execCommand: 'deploy.sh')
                        ]
                    )]
                )
            }
        }
    }
}
