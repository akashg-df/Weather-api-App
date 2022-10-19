pipeline {
    agent {      
          stage('Clean Build') {
                dir("android") {
                    sh 'ls -al'
                    sh './gradlew clean'
                }   
        }
        
        stage('Build debug ') {
             dir("android") {
                sh './gradlew assembledebug'
            }
        }
      } catch (caughtError) { 
    
    err = caughtError
    currentBuild.result = "FAILURE"

} finally {
    
    if(currentBuild.result == "FAILURE"){
              sh "echo 'Build FAILURE'"
    }else{
         sh "echo 'Build SUCCESSFUL'"
    }
   
}
        
