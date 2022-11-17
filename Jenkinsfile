pipeline {
	 agent any
	    parameters {
	        booleanParam(name: "$build.gradle", defaultValue: false)
	        choice(name: "$build.gradle", choices: ["", "WS", "Debug", "Release"])
	          }
	  stages {
	     stage("Build") {
	            steps {
	                bat "./gradlew build"
	            }
	        }
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
