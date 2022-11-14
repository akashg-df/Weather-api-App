pipeline{
  agent any
	      stages{
	          stage("SCM Checkout"){
	              steps{
	                     git 'https://github.com/akashg-df/Weather-api-App'
	                   }
	                }
          
          stages('Setup parameters') {
            steps {
                    properties([
                        parameters([
                            choice(
                                defaultValue: 'RELEASE', 
                                choices: ['RELEASE', 'DEBUG'], 
                                name: 'BUILD_CONFIG'
                            ),
                        ])
                    ])
           stages('Build release'){
            when {
                expression {
                   return params.BUILD_CONFIG == 'RELEASE'
                }
            }      
        }
        stages('Build debug'){
            when {
                expression {
                   return params.BUILD_CONFIG == 'DEBUG'
                }
            }
        }
          }
          }
    }
}
