pipeline{
  agent any
 
  stages{
      stage("SCM Checkout"){
          steps{
          git 'https://github.com/akashg-df/Weather-api-App'
          }
      }
     parameters {
  choice choices: ['', 'RELEASE', 'DEBUG'], name: '$build.gardle'
}
  stage("Android Release"){
         if params.build.gradle = Release 
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
  
