pipeline {

    stages {
        stage("Checkout") {
            steps {
                sh('make test')
            }
        }
        stage("Test") {
            steps {
                sh('make test')
	    }
        }
	stage("Deploy to Staging") {
	    when {
		sh('make test')
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
	        sh('make test')
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
