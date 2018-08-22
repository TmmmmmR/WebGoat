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
            }
        }
        stage('Deploy for production') {
            when {
                branch 'production'  
            }
            steps {
                sh 'echo "TMR"'
            }
        }
    }
}
