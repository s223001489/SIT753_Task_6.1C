pipeline {
   agent any
   stages {
       stage('Build') {
           steps {
               echo 'Building the code...'
               // Use Maven for building (e.g., sh 'mvn clean package')
           }
       }
       stage('Unit and Integration Tests') {
           steps {
               echo 'Running unit and integration tests...'
               // Use JUnit or TestNG for tests (e.g., sh 'mvn test')
           }
       }
       stage('Code Analysis') {
           steps {
               echo 'Running code analysis...'
               // Integrate SonarQube for code analysis (e.g., sh 'sonar-scanner')
           }
       }

       stage('Security Scan') {
           steps {
               echo 'Performing security scan...'
               // Use OWASP ZAP or SonarQube for security scan
           }
       }
       stage('Deploy to Staging') {
           steps {
               echo 'Deploying to staging server...'
               // Use AWS CodeDeploy or similar for deployment
           }
       }
       stage('Integration Tests on Staging') {
           steps {
               echo 'Running integration tests on staging...'
               // Execute integration tests on staging environment
           }
       }
       stage('Deploy to Production') {
           steps {
               echo 'Deploying to production server...'
               // Deploy to production using deployment tools
           }
       }
   }
   post {
       success {
           script {
               mail (
                   subject: 'Pipeline Success - Application Deployed',
                   body: 'Pipeline completed successfully.',
                   to: 'rsrivarshini313@gmail.com'
               )
           }
           echo 'Pipeline succeeded! Application deployed successfully.'
       }
       failure {
           script {
               mail (
                   subject: 'Pipeline Failure - Application Deployment Failed',
                   body: 'Pipeline failed. Please check the logs.',
                   to: 'rsrivarshini313@gmail.com'
               )
           }
           echo 'Pipeline failed! Please check the build logs.'
       }
   }
}
