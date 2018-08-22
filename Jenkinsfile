/*
** Demo DevSecOps **
*/

node {
   
   stage('Checkout') {
   }
   
   stage('Build') {
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
   }
   
   
   //Get approval from user before deployment
    input 'Ready to Deploy??'

    stage("Deploy"){
    //Deploy Code here
    }
}


