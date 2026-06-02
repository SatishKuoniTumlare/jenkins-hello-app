pipeline {
    agent any

    // 1. Tell Jenkins to use the Node version you configured in your Global Tools
    tools {
        nodejs 'node24' // Make sure this matches your exact tool name in Jenkins
    }

    stages {
        stage('Fetch') {
            steps {
                git changelog: false, poll: false, url: 'https://github.com/SatishKuoniTumlare/jenkins-hello-app.git'
            }
        }

        // 2. Add a stage to download your node_modules (including Vite)
        stage('Install Dependencies') {
            steps {
                sh 'npm ci'
            }
        }

        // 3. Change "dev" to "build" to generate the final production files
        stage('Compile & Build') {
            steps {
                sh "npm run build"
            }
        }
    }
}