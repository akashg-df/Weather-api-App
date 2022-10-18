pipeline{
    agent any
    tools{
   Android sdk 'Android sdk'
    }
    stages{
        stage("SCM Checkout"){
            steps{
            git 'https://github.com/akashg-df/Weather-api-App.git'
            }
        }
        stage("Android build"){
            steps{
                Task 'assembledebug'
            }
        }
    }
}
