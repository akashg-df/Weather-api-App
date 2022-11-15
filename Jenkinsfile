pipeline{
  agent any
 
  stages{
      stage("SCM Checkout"){
          steps{
          git 'https://github.com/akashg-df/Weather-api-App'
          }
      }
  stages{
      stage ("parameters") {
      choice choices: ['', 'RELEASE', 'DEBUG'], 
      name: '$build.gardle'
     }
      if
      stage("Android Release"){
          steps{
              bat './gradlew assembleRelease assembledebug'
          }
         
      }
      else
         stage("Android Debug"){
            steps{
                bat 'gradlew assembledebug'
            }
         
        }
   stage('Unit test') {
    steps {
      // Compile and run the unit tests for the app and its dependencies
      bat './gradlew testDebugUnitTest'
    }
  }  
  }
  }
}
