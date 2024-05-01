pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Change to the myproject directory
                    dir('/Users/vv/.jenkins/workspace/My_Pipeline/myproject') {
                        // Execute Maven commands to build the project
                        def mvnHome = tool 'Maven'
                        sh "${mvnHome}/bin/mvn clean package"
                    }
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    // Change to the myproject directory
                    dir('/Users/vv/.jenkins/workspace/My_Pipeline/myproject') {
                        // Execute Maven commands to run unit tests and integration tests
                        def mvnHome = tool 'Maven'
                        sh "${mvnHome}/bin/mvn test integration-test"
                    }
                }
            }
        }

        stage('Code Analysis') {
            steps {
                // Use a code analysis tool like SonarQube, Checkstyle, FindBugs, PMD, etc.
                // Example:
                sh "mvn sonar:sonar"
            }
        }

        stage('Security Scan') {
            steps {
                // Use a security scanning tool like OWASP Dependency-Check, SonarQube with Security Plugin, etc.
                // Example:
                sh "mvn verify"
            }
        }

        stage('Deploy to Staging') {
            steps {
                // Deploy the application to a staging server (e.g., AWS EC2 instance)
                // Example:
                sh "scp target/myproject.jar user@staging-server:/path/to/deploy"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on the staging environment
                // Example:
                sh "ssh user@staging-server 'java -jar /path/to/deploy/myproject.jar --run-integration-tests'"
            }
        }

        stage('Deploy to Production') {
            steps {
                // Deploy the application to a production server (e.g., AWS EC2 instance)
                // Example:
                sh "scp target/myproject.jar user@production-server:/path/to/deploy"
            }
        }
    }

    post {
        success {
            echo "Pipeline succeeded! Application deployed to production."
        }
        failure {
            echo "Pipeline failed! Please check the build logs for errors."
        }
    }
}
