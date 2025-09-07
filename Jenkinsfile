pipeline {
    agent any

    environment {
        NODE_ENV = 'development'
    }

    tools {
        nodejs "NodeJS_18" // Jenkins NodeJS tool name (set in Jenkins global tools config)
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/durgaprasadraju/solar-system-gitea.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Lint') {
            steps {
                sh 'npm run lint'  // Make sure lint script exists in package.json
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'  // If you have a build step
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying application..."
                // Add your deploy logic here, like:
                // sh './deploy.sh' or calling a PM2 command or Docker deployment
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
