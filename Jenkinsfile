pipeline{
  agent any
 
  stages{
      stage("SCM Checkout"){
          steps{
          git 'https://github.com/akashg-df/Weather-api-App'
          }
      }
       stage("Android Release"){
         steps{
              bat './gradlew assembleRelease'
              }
         
      }
      
//          stage("Android Debug"){
//             steps{
//                 bat 'gradlew assembledebug'
//             }
         
//         }
 
  

   stage('Unit test') {
    steps {
      // Compile and run the unit tests for the app and its dependencies
      bat './gradlew testDebugUnitTest'
    }
  }  
  
  }
}
 


