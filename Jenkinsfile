pipeline{
	    agent any
	   
	    stages{
	        stage("SCM Checkout"){
	            steps{
	            git 'https://github.com/akashg-df/Weather-api-App'
	            }
	        }
          stage("Build"){
               if (params.BUILD_CONFIG == 'release') {
               bat './gradlew clean assembleRelease' // builds app/build/outputs/apk/app-release.apk file
               } else {
               bat './gradlew clean assembleDebug' // builds app/build/outputs/apk/app-debug.apk
                }
             }
	        
// 	        stage("Android Release"){
// 	            steps{
// 	                bat './gradlew clean assembleDebug assembleRelease'
// 	            }
	           
// 	        }
	        
	//          stage("Android Debug"){
	//             steps{
	//                 bat 'gradlew assembledebug'
	//             }
	           
	//         }
// 	     stage('Unit test') {
// 	      steps {
// 	        // Compile and run the unit tests for the app and its dependencies
// 	        bat './gradlew testDebugUnitTest'
// 	      }
// 	    }
	        stage("Archive"){
    if (params.BUILD_CONFIG == 'release') {
        archiveArtifacts artifacts: 'app/build/outputs/apk/**/app-release.apk', excludes: 'app/build/outputs/apk/*-unaligned.apk'
    } else {
        archiveArtifacts artifacts: 'app/build/outputs/apk/**/app-debug.apk', excludes: 'app/build/outputs/apk/*-unaligned.apk'
    }
  }
	        
	    }
	}
	   

