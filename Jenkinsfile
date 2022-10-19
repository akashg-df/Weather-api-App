
def err = null
try {
  
    Android {
      
        stage('Preparation') { 
            git credentialsId: 'Gupta@092', url: 'gh repo clone akashg-df/Weather-api-App'
        }
      
        stage('Dependencies') {
                sh 'Users/akash/AppData/Local/Android/Sdk
                sh 'export JAVA_HOME=/Java/jdk-11.0.16
                 
        }
        
        stage('Clean Build') {
                dir("android") {
                    sh 'ls -al'
                    sh './gradlew clean'
                }   
        }
        
        stage('build.gradle ') {
            dir("android") {
                sh './gradlew assembleRelease'
            }
        }
      
        stage('Compile') {
            archiveArtifacts artifacts: app\build\outputs\apk\debug\*.apk       
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

