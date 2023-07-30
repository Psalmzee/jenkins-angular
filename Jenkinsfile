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
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build -- --prod'
            }
        }

        stage('Test') {
            steps {
                sh 'npm run test'
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
