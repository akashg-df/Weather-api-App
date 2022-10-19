pipeline { 
    agent any 
    Android {  
        C:\Users\akash\AppData\Local\Android\Sdk

    }
    stages {
        stage('Build') { 
            steps { 
                sh 'build.gradle' 
            }
        }
   
        stage('Deploy') {
            steps {
                sh 'build.gradle'
            }
        }
    }
}
