pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the Git repository into the Jenkins workspace
                git 'https://github.com/s223001489/SIT753_Task_6.1C.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    // Define the project directory path relative to the Jenkins workspace
                    def projectDir = "${WORKSPACE}/SIT753_Task_6.1C"

                    // Check if project directory exists
                    if (fileExists(projectDir)) {
                        // Change to the project directory containing pom.xml
                        dir(projectDir) {
                            // Execute Maven command to build the project
                            def mvnHome = tool 'Maven'
                            sh "${mvnHome}/bin/mvn clean package"
                        }
                    } else {
                        error "Project directory not found in the Jenkins workspace!"
                    }
                }
            }
        }

        stage('Unit Tests') {
            steps {
                script {
                    // Define the project directory path relative to the Jenkins workspace
                    def projectDir = "${WORKSPACE}/SIT753_Task_6.1C"

                    // Check if project directory exists
                    if (fileExists(projectDir)) {
                        // Change to the project directory containing pom.xml
                        dir(projectDir) {
                            // Execute Maven command to run unit tests
                            def mvnHome = tool 'Maven'
                            sh "${mvnHome}/bin/mvn test"
                        }
                    } else {
                        error "Project directory not found in the Jenkins workspace!"
                    }
                }
            }
        }

        stage('Integration Tests') {
            steps {
                script {
                    // Define the project directory path relative to the Jenkins workspace
                    def projectDir = "${WORKSPACE}/SIT753_Task_6.1C"

                    // Check if project directory exists
                    if (fileExists(projectDir)) {
                        // Change to the project directory containing pom.xml
                        dir(projectDir) {
                            // Execute Maven command to run integration tests
                            def mvnHome = tool 'Maven'
                            sh "${mvnHome}/bin/mvn verify"
                        }
                    } else {
                        error "Project directory not found in the Jenkins workspace!"
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Define the project directory path relative to the Jenkins workspace
                    def projectDir = "${WORKSPACE}/SIT753_Task_6.1C"

                    // Check if project directory exists
                    if (fileExists(projectDir)) {
                        // Change to the project directory containing pom.xml
                        dir(projectDir) {
                            // Example: Deploy the application to a server
                            // Replace this with your deployment command
                            sh "echo 'Deploying to server...'"
                        }
                    } else {
                        error "Project directory not found in the Jenkins workspace!"
                    }
                }
            }
        }
    }

    post {
        success {
            echo "Pipeline succeeded! Project built, tested, and deployed."
        }
        failure {
            echo "Pipeline failed! Please check the build logs for errors."
        }
    }
}
