
//   def branch = readFile('branch').trim()
// if (branch == master) {
  
// }
  
//     node {
      
//         stage('Preparation') { 
//             git credentialsId: 'Gupta@092', url: 'https://github.com/akashg-df/Weather-api-App.git'
//         }
    
      
//         stage('Clean Build') {
//                 dir("android") {
//                     sh "pwd"
//                     sh 'ls -al'
//                     sh './gradlew clean'
//                 }   
//         }
        
//         stage('Build.gradle ') {
//                 dir("android") {
//                 sh './gradlew assembleRelease'
//             }
//         }
      
//         stage('Compile') {
//             archiveArtifacts artifacts: '**/*.apk'           
//         }
//     }
  class Constants {

    static final String MASTER_BRANCH = 'master'

    static final String debug= 'Debug'
    static final String Release = 'Release'
  }

def getBuildType() {
    switch (env.BRANCH_NAME) {
        case Constants.MASTER_BRANCH:
            return Constants.RELEASE
        default:
            return Constants.Debug
    }
}

