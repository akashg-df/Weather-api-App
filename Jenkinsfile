pipeline{
  stage('deploy'){
    agent { label 'slave' }
  steps{
    script{
      if [ "$build.gradle" = debug ];
      then 
        echo 'restart not required'
      elif [ "$build.gradle" = Release ];
      then
        echo "restart required"
        //need to invoke another jenkins pipeline-B here
      fi
    }
  }
