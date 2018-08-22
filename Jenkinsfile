/*
** Demo DevSecOps **
*/

node {
      stage('Checkout') {
      sh 'echo "Step x"'
   }
   
   stage('Build') {
      sh 'echo "Step x"'
   }
   
  stage('Tests') {
      steps {
        parallel(
          "Unit Tests": {
            sh 'echo "Unit Tests"'
            
          },
          "Feature tests": {
            sh 'echo "Feature Tests"'
          }
        )
      }
  }

   stage("Results"){
      sh 'echo "Step x"'
   }
   
   
   //Get approval from user before deployment
    input 'Ready to Deploy??'

    stage("Deploy"){
      sh 'echo "Step x"'
    }
}


