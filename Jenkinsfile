pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v $HOME/.m2:/root/.m2'
        }
    }
        stages {
                
        stage('Build') {
            steps {
                sh 'mvn -B'
            }
        }
                
        stage('Unit Test') {
            steps {
                sh 'echo "Running Unit Tests"'
            }
        }

        stage('Deliver to developement') {
            when {
                branch 'develop' 
            }
            steps {
                echo 'I only execute on the dev branch' 
            }
        }
            
        stage('Deploy') {
            when {
                expression { BRANCH_NAME == 'production' && (currentBuild.result == null || currentBuild.result == 'SUCCESS') }
            }
            steps {
                // Add confirmation message before deploying
                sh 'echo "[+] Deploy to production"'
            }
        }
    }
        post {
        success {
            sh 'echo "[-] Success ebug message ..."'
        }
        failure {
            sh 'echo "[-] Failure message ..."'
        }
        unstable {
            sh 'echo "[-] Unstable message ..."'
        }
        fixed {
            sh 'echo "[-] Fixed message goes here ..."'
        }
        always {
            sh 'echo "[-] Record test results (fallback) ..."'
            //  ....
            //junit '**/target/*-reports/*.xml'
        }
        cleanup {
            script {
                sh 'echo "[+] Cleanning up ..."'
            }
        }
    }
}
