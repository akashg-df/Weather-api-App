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
                                name: '$Build.gardle'
                            ),
                        ])
                    ])
			 stage('Build release'){
            when {
                expression {
                   return params.'$Build.gardle' == 'RELEASE'
                }
            }
             steps{
                script {
                   def Build.gardle = tool name: 'Build.gardle', type: 'hudson.plugins.Build.gardle.Build.gardleInstallation'
                   bat "\"${Build.gardle}\" /Source/project-GRDK.sln /t:Rebuild /p:configuration=\"Release\""
                 }
             }
        }
        stage('Build debug'){
            when {
                expression {
                   return params.'$Build.gardle' == 'DEBUG'
                }
            }
            steps{
                script {
                   def msbuild = tool name: 'MSBuild', type: 'hudson.plugins.msbuild.MsBuildInstallation'
                     bat "\"${Build.gardle}\" /Source/project-GRDK.sln /t:Rebuild /p:configuration=\"Debug \""
                 }
             }
        }
 	     }
            }
          }
        }
}
