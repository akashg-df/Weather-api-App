pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh './gradlew clean assembleDebug assembleRelease'

            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
