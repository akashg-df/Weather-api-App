pipeline {
	 agent any
	    parameters {
	     choice(name: "$build.gradle", choices: ["", "Debug", "Release"])
	          }
	  stages {
	      stage("Debug) {
	            parallel {
	                stage('Debug') {
	                    when { expression { !params.Debug } }
	                    steps {
	                       bat "./gradlew assembleDebug"
	                    }
	                }
	   stage("Release") {
	                    when { expression { params.RELEASE } }
	                    steps {
	                        bat "./gradlew assembleRelease"
	                    }
	                }
	            }
	        }              
	      }	
	    }
	}
