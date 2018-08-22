node {
      stage('Checkout') {
      steps {
        sh 'echo "X Step"'
      }
   }
   
   stage('Build') {
      steps {
        sh 'echo "X Step"'
      }
   }
   
   stage('Run Tests') {
            parallel {
                stage('Test On Windows') {
                    agent {
                        label "windows"
                    }
                    steps {
                        sh 'echo "X Step"'
                    }
                }
                stage('Test On Linux') {
                    agent {
                        label "linux"
                    }
                    steps {
                        sh 'echo "X Step"'
                    }
                }
            }
   }

   stage("Results"){
      steps {
        sh 'echo "X Step"'
      }
   }
   
   
   //Get approval from user before deployment
    input 'Ready to Deploy??'

    stage("Deploy"){
      steps {
        sh 'echo "X Step"'
      }
    }
}
