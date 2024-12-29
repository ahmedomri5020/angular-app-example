pipeline {
    agent any

    environment {
        PATH = "/usr/local/bin:$PATH"  // Adjust the path to where Node.js and Angular CLI are installed
    }

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
                    // Install dependencies (ensure npm and Angular CLI are available)
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
                    // Run unit tests (using Angular CLI, set headless browser for Jenkins)
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

