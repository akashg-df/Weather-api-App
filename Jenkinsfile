pipeline{
    agent any
    
    stages{
        stage("SCM Checkout"){
            steps{
            git 'https://github.com/akashg-df/Weather-api-App'
            }
        }
        stage("Android build"){
            steps{
                bat 'gradlew assembleRelease'
            }
        }
    
     stage('Unit test') {
      steps {
        // Compile and run the unit tests for the app and its dependencies
        bat './gradlew testDebugUnitTest'
      }
    }
      }
    finally {
    
    if(currentBuild.result == "FAILURE"){
              bat "echo 'Build FAILURE'"
    }else{
         bat "echo 'Build SUCCESSFUL'"
    }
}
