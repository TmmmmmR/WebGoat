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
                sh 'echo "TMR"'
            }
        }
        stage('Deliver for development') {
            when {
                branch 'development' 
            }
            steps {
                sh 'echo "TMR"'
                input message: 'Deploy to Dev Environnement ? (Click "Proceed" to continue)'
            }
        }
        stage('Deploy for production') {
            when {
                branch 'production'  
            }
            steps {
                input message: 'Deploy to Dev Environnement ? (Click "Proceed" to continue)'
            }
        }
    }
}
