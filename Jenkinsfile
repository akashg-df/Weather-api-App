
pipeline {
    agent {
        // Run on a build agent where we have the Android SDK installed
        label 'android'
    }
    environment {
        // Fastlane Environment Variables
        PATH = "$HOME/.fastlane/bin:" +
                "$HOME/.rvm/gems/ruby-2.5.3/bin:" +
                "$HOME/.rvm/gems/ruby-2.5.3@global/bin:" +
                "$HOME/.rvm/rubies/ruby-2.5.3/bin:" +
                "/usr/local/bin:" +
                "$PATH"
        LC_ALL = "en_US.UTF-8"
        LANG = "en_US.UTF-8"

        VERSION_NAME = ""
        VERSION_SUFFIX = ""
        APP_VERSION_NAME = ""
        VERSION_CODE = ""
        DROPBOX_FOLDER = ""
        PROGUARD_ENABLED = ""
        JIRA_PROJECT_KEY = ""
        PROJECT_NAME = env.JOB_NAME.tokenize("/").first().replaceAll(" Android", "")
    }
    options {
        // Stop the build early in case of compile or test failures
        skipStagesAfterUnstable()
    }
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
    }
    
}
