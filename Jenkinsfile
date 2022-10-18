pipeline { 
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') { 
            steps { 
                sh 'assembledebug' 
            }
        }
   
        stage('Deploy') {
            steps {
                sh 'assembledebug'
            }
        }
    }
}
