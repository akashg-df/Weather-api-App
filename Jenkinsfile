 pipeline{
 stages{
   agent any
          stage("SCM Checkout"){
	              steps{
	                     git 'https://github.com/akashg-df/Weather-api-App'
	                   }
	                }
          
          stage('Setup parameters') {
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
        }
        stage('Build debug'){
            when {
                expression {
                   return params.'$Build.gardle' == 'DEBUG'
                }
            }
        }
          
        }
    }
}
