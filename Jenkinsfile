pipeline {
    agent { label 'myLabel' }
    environment {
        GIT_TAG = sh(returnStdout: true, script: 'git describe --always').trim()
    }
    stages {
        stage("Checkout") {
            steps {
                checkout scm
            }
        }
        stage("Test") {
            steps {
                sh('make test')
	    }
        }
	stage("Deploy to Staging") {
	    when {
		buildingTag()
	    }
	    environment {
		ENVIRONMENT = 'staging'
	    }
	    steps {
		sh('make deploy')
	    }
	}
	stage("Smoketest") {
	    steps {
                sh('make smoketest')
	    }
        }
	stage("Deploy to Production") {
	    when {
	        buildingTag()
            }
            environment {
	        ENVIRONMENT = 'production'
            }
            steps {
	        sh('make deploy')
            }
        }
    }
}
