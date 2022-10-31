pipeline{
    agent any
    
    stages{
        stage("SCM Checkout"){
            steps{
            git 'https://github.com/akashg-df/Weather-api-App'
            }
        }
        stage("Android build"){
            steps{
                bat 'gradlew assembleRelease'
            }
        }
    }
}
