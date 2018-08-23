@Library('jenkins-shared-libraries') _

pipeline {
/*    agent {
        node {
            label 'alpine:jdk8-mvn-3.5'
            customWorkspace workspace().getUniqueWorkspacePath()
        }
    }
    parameters {
        booleanParam(defaultValue: true, description: 'Send email notification?', name: 'NOTIFY_EMAIL')
        booleanParam(defaultValue: true, description: 'Trigger strongbox-os-build?', name: 'TRIGGER_OS_BUILD')
    }
    options {
        timeout(time: 2, unit: 'HOURS')
        disableConcurrentBuilds()
    }
*/
    stages {
        stage('Build')
        {
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
                if (env.BRANCH_NAME == 'master') {
                        echo 'I only execute on the master branch'
                } else {
                        echo 'I execute elsewhere'
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
