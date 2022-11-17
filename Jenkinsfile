pipeline {
	 agent any
	    parameters {
	        booleanParam(name: "RELEASE", defaultValue: false)
	        choice(name: "build.gradle", choices: ["", "WS", "Debug", "Release"])
	          }
	  stages {
	     stage("Build") {
	            steps {
	                sh "./gradlew build"
	            }
	        }
	  stage("Debug) {
	            parallel {
	                stage('Pre-Release') {
	                    when { expression { !params.Debug } }
	                    steps {
	                        sh "./gradlew Debug"
	                    }
	                }
	   stage("Release") {
	                    when { expression { params.RELEASE } }
	                    steps {
	                        sh "./gradlew release"
	                    }
	                }
	            }
	        }              
	      }	
	    }
	}
