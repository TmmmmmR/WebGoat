pipeline {
   agent any
   stages {
   stage('Check Out') {
      steps {
        sh 'echo "X Step"'
      }
   }
   
   stage('Build') {
      steps {
        sh 'echo "X Step"'
      }
   }
   
   stage('Tests') {
      steps {
        sh 'echo "X Step"'
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
}
