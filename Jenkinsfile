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
                                name: 'Build.gardle'
                            ),
                        ])
                    ])
	 stage('Build release'){
            when {
                expression {
                   return params.'Build.gardle' == 'RELEASE'
                }
            }
             steps{
                script {"
                  bat ./"${params.Build.gardle}"
                 }
             }
        }
        stage('Build debug'){
            when {
                expression {
                   return params.'Build.gardle' == 'DEBUG'
                }
            }
            steps{
                script {
               bat ./"${ params.Build.gardle}"
                 }
             }
        }
 	                       }
            }
          }
        }
}
