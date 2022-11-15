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
  stage("Android Release"){
         if steps{
              bat './gradlew assembleRelease'
          else
               bat '/gradlew assembledebug'
          }
         
      }
      else
         stage("Android Debug"){
            steps{
                bat 'gradlew assembledebug'
            }
         
        }
 }
  }
}
