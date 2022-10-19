
pipeline {
    agent none
    environment {
        VERSION = sh 'C:\Users\akash\AppData\Local\Android\Sdk'
    }
}
  
    Android {
      
        stage('Preparation') { 
            git credentialsId: 'Gupta@092', url: 'gh repo clone akashg-df/Weather-api-App'
        }
      
        stage('Dependencies') {
            
             implementation 'androidx.appcompat:appcompat:1.4.1'
      implementation 'com.google.android.material:material:1.5.0'
    implementation 'androidx.constraintlayout:constraintlayout:2.1.3'
    testImplementation 'junit:junit:4.13.2'
    androidTestImplementation 'androidx.test.ext:junit:1.1.3'
    androidTestImplementation 'androidx.test.espresso:espresso-core:3.4.0'
                 
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

