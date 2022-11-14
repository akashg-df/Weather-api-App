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
                                name: 'BUILD_CONFIG'
                            ),
                        ])
                    ])
                }
            }
          
           stage('Build release'){
            when {
                expression {
                   return params.BUILD_CONFIG == 'RELEASE'
                }
            }
//            
        }
        stage('Build debug'){
            when {
                expression {
                   return params.BUILD_CONFIG == 'DEBUG'
                }
            }
        }
          }
    }
}
