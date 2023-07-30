pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                bat 'npm run build -- --configuration=production'
            }
        }

        stage('Test') {
            steps {
                bat 'npm run test'
            }
        }

        stage('Create Artifact') {
            steps {
                archiveArtifacts(artifacts: 'dist/**') // This will archive all files in the 'dist' directory as the build artifact
            }
        }
    }

    post {
        always {
            cleanWs() // Clean up the workspace after the build is done
        }
    }
}
