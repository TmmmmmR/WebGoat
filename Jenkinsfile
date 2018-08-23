pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "TMR"'
            }
        }
        
        stage('Unit Test) {
            steps {
                sh 'echo "Running Unit Tests"'
            }
        }
              
        stage('Deliver for development') {
            when {
                branch 'development' 
            }
            steps {
                sh 'echo "Deploy to Prod. Env."' 
            }
        }
              
        stage('Functionel Testing on Development Env.') {
            when {
                branch 'development' 
            }
            steps {
                sh 'echo "Deploy to Prod. Env."' 
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
