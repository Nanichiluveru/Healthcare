pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pull the latest code from GitHub
                git branch: 'main', url: 'https://github.com/yourname/frontend-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install Node.js packages
                sh 'npm install'
            }
        }

        stage('Build Frontend') {
            steps {
                // Build the project (Vite or React)
                sh 'npm run build'
            }
        }

        stage('Archive Build') {
            steps {
                // Save dist/build folder as artifact
                archiveArtifacts artifacts: 'dist/**', fingerprint: true
            }
        }

        stage('Deploy to Local Server') {
            steps {
                echo 'Copying build files to web directory...'
                // Change path to your local web folder (Windows or Linux)
                sh 'cp -r dist/* /var/www/html/myapp/'
            }
        }
    }

    post {
        success {
            echo '✅ Frontend build and deployment successful!'
        }
        failure {
            echo '❌ Build or deploy failed!'
        }
    }
}