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
            steps {
                    {
                            script
                            {
                                    if(BRANCH_NAME == 'master'){
                                            sh 'echo "Code Analysis for master branch"'
                                    }
                                    else {
                                            if(BRANCH_NAME.startsWith("PR-")){
                                                    sh 'echo "Code Analysis for master branch"'
                                            }
                                            else {
                                                    echo "This step is skipped for branches other than master or PR-*"
                                            }
                                    }
                            }
                    }
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
            script {
                if(BRANCH_NAME == 'master' && params.TRIGGER_OS_BUILD) {
                    sh 'echo "Debug message ..."'
                }
            }
        }
        failure {
            script {
                if(params.NOTIFY_EMAIL) {
                    sh 'echo "Debug message ..."'
                }
            }
        }
        unstable {
            script {
                if(params.NOTIFY_EMAIL) {
                    sh 'echo "Debug message ..."'
                }
            }
        }
        fixed {
            script {
                if(params.NOTIFY_EMAIL) {
                   sh 'echo "Debug message ..."'
                }
            }
        }
        always {
            // (fallback) record test results even if withMaven should have done that already.
            //junit '**/target/*-reports/*.xml'
        }
        cleanup {
            script {
                sh 'echo "Debug message ..."'
            }
        }
    }
}
