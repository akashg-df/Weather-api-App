
  def branch = readFile('branch').trim()
if (branch == master) {
  
}
  
    node {
      
        stage('Preparation') { 
            git credentialsId: 'Gupta@092', url: 'https://github.com/akashg-df/Weather-api-App.git'
        }
    
      
        stage('Clean Build') {
                dir("android") {
                    sh "pwd"
                    sh 'ls -al'
                    sh './gradlew clean'
                }   
        }
        
        stage('Build.gradle ') {
                dir("android") {
                sh './gradlew assembleRelease'
            }
        }
      
        stage('Compile') {
            archiveArtifacts artifacts: '**/*.apk'           
        }
    }
  
 catch (caughtError) { 
    
    err = caughtError
    currentBuild.result = "FAILURE"

} finally {
    
    if(currentBuild.result == "FAILURE"){
              sh "echo 'Build FAILURE'"
    }else{
         sh "echo 'Build SUCCESSFUL'"
    }
   
 }}
