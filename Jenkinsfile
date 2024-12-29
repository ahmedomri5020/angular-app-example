pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                // Cloning the repository
                git 'https://github.com/ahmedomri5020/angular-app-example.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install dependencies if you need to (example: using npm for Angular)
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build the application
                    sh 'ng build --prod'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run unit tests (example: using Angular's built-in testing framework)
                    sh 'ng test --watch=false --browsers=ChromeHeadless'
                }
            }
        }

        stage('Archive Results') {
            steps {
                // Archive the test results or any other relevant files
                archiveArtifacts artifacts: '**/target/*.test-*.xml', allowEmptyArchive: true
            }
        }
    }
}

