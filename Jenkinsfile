pipeline {
        agent any
        stages {
        stage('Build') {
            steps {
                sh 'echo "Building the application"'
            }
        }

        stage('Unit Test') {
            steps {
                sh 'echo "Running Unit Tests"'
            }
        }

        stage('Code Analysis') {
            when {
                branch 'master' 
            }
            steps {
                echo 'I only execute on the master branch' 
            }
        }
            
        stage('Deploy') {
            when {
                expression { BRANCH_NAME == 'master' && (currentBuild.result == null || currentBuild.result == 'SUCCESS') }
            }
            steps {
                sh 'echo "Deploy to production"'
            }
        }
    }
        post {
        success {
            sh 'echo "Debug message ..."'
        }
        failure {
            sh 'echo "Debug message ..."'
        }
        unstable {
            sh 'echo "Debug message ..."'
        }
        fixed {
            sh 'echo "Debug message ..."'
        }
        always {
            // (fallback) record test results even if withMaven should have done that already.
            //junit '**/target/*-reports/*.xml'
            sh 'echo "Debug message ..."'
        }
        cleanup {
            script {
                sh 'echo "Debug message ..."'
            }
        }
    }
}
