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
            
        stage('Deploy to production') {
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
            //slackSend (color: '#00aa5b', message: "Build OK de la branche ${env.GIT_BRANCH}, commit: ${env.GIT_COMMIT}", channel: "#pic-ci")
        }
        failure {
            //slackSend (color: '#a30000', message: "Build KO de la branche ${env.GIT_BRANCH}, commit: ${env.GIT_COMMIT}", channel: "#pic-ci")
        }
        unstable {
            //slackSend (color: '#ffaa00', message: "Build Unstable de la branche ${env.GIT_BRANCH}, commit: ${env.GIT_COMMIT}", channel: "#pic-ci")
        }
        fixed {
            sh 'echo "[-] Fixed debug message goes here ..."'
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
