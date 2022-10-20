
pipeline {
      agent {
            node {
                label "master"
      stages {
        stage('Start Build') {
            steps {
                bitbucketStatusNotify(buildState: 'INPROGRESS')
            }
        }
               stage('Copy Local Properties') {
            steps {
                script {
                    def projName = PROJECT_NAME.replaceAll(" ", "_").toLowerCase()
                    sh "cp ~/Documents/${projName}/local.properties ."
                }
            }
        }
        
        stage('Build App') {
            steps {
                // Clean and assemble APKs
                sh './gradlew clean assembleDebug assembleRelease'

               }
            }
        }
       
        }
        stage('Archive Files') {
            steps {
                // Archive the APKs so that they can be downloaded from Jenkins
                echo 'Archiving APKs...'
                archiveArtifacts '**/*.apk'

                script {
                    if (PROGUARD_ENABLED == "true") {
                        echo 'Archiving Mappings...'
                        archiveArtifacts '**/mapping.txt'
                    }

                    if (env.BRANCH_NAME.startsWith("release")) {
                        echo 'Archiving AABs...'
                        archiveArtifacts '**/*.aab'
                    }
                }
            }
        }
       
       
        stage('Finished') {
            steps {
                echo 'Finished'
            }
        }
    
    

