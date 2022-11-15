pipeline{
	    agent any
	   
	    stages{
	        stage("SCM Checkout"){
	            steps{
	            git 'https://github.com/akashg-df/Weather-api-App'
	            }
	        }
	         
          stage('Setup parameters') {
            steps {
                script { 
                    properties([
                        parameters([
                            choice(
                                defaultValue: 'RELEASE', 
                                choices: ['RELEASE', 'DEBUG'], 
                                name: 'build.gradle'
                            ),
                        ])
                    ])
			 stage('Build release'){
            when {
                expression {
                   return params.build.gardle == 'RELEASE'
                }
            }
            steps{
                script {
                    def msbuild = tool name: 'MSBuild', type: 'hudson.plugins.msbuild.MsBuildInstallation'
                    bat "\"${build.gardle}\" =\"gradlew assembleRelease \""
                }
            }
        }
        stage('Build debug'){
            when {
                expression {
                   return params.build.gardle == 'DEBUG'
                }
            }
            steps{
                script {
                    def msbuild = tool name: 'MSBuild', type: 'hudson.plugins.msbuild.MsBuildInstallation'
                    bat "\"${build.gardle}\"=\"gradlew assembleRelease \""
                }
            }
        }
                }
            }
          }
        }}
