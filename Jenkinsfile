pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "TMR"'
            }
        }
        stage('Test') {
            steps {
                parallel(
                    "Unit Tests": {
                        sh 'echo "Unit Tests"'
                    },
                    "Feature tests": {
                        sh 'echo "Feature Tests"'
                    }
                )
            }
        }
        stage('Deliver for development') {
            when {
                branch 'development' 
            }
            steps {
                input message: 'Deploy to Dev Environnement ? (Click "Proceed" to continue)'
                sh 'echo "Deploy to Dev Env."'
                sh 'echo "Running Automated Infra. Security Scans"'
            }
        }
        stage('Deploy for production') {
            when {
                branch 'production'  
            }
            steps {
                sh 'echo "Deploy to Prod. Env."'
                sh 'echo "Running Automated Infra. Security Scans"'
            }
        }
    }
}
