pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests'
                echo 'Running integration tests'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis using sonarqube'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server (AWS EC2)'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server (AWS EC2)'
            }
        }
    }
    
  post {
    always {
        script {
            echo "Sending email notification..."
            emailext body: "Pipeline ${currentBuild.result}: ${env.BUILD_URL}",
                     subject: "Pipeline ${currentBuild.result}: ${env.JOB_NAME}",
                     to: 'rsrivarshini313@gmail.com',
                     attachLog: true,
                     attachmentsPattern: '*'
            echo "Email notification sent."
        }
    }
}
