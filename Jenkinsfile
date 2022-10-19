pipeline {
    agent {      
        stage('Dependencies') {
                sh 'export JAVA_HOME=Java\jdk-11.0.161'
                sh 'echo $JAVA_HOME'
        }
        
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
      
        stage('Compile') {
            archiveArtifacts artifacts: '**/*.apk', fingerprint: true, onlyIfSuccessful: true            
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
        
