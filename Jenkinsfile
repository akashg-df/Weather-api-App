pipeline {
    agent {      
          stage('Clean Build') {
                dir("android") {
                    sh 'ls -al'
                    sh './gradlew clean'
                }   
        }
        
        stage('Build debug ') {
             dir("android") {
                sh './gradlew assembledebug'
            }
        }
    }
}
