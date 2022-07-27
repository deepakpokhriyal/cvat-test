pipeline {
    environment {
     BRANCH_NAME = "${GIT_BRANCH.split("/")[1]}"
  }
    agent any
    stages {
       stage('Build') {
            steps {
               script {
                    if (env.BRANCH_NAME == 'master') 
                    {
                        git url: 'https://github.com/deepakpokhriyal/cvat-test.git', branch: 'master'
                          sh "Building in ${env.BRANCH_NAME}"
                      //  sh "docker-compose -f docker-compose.yml -f docker-compose.dev.yml build"
                    } 
                    if (env.BRANCH_NAME == 'dev') 
                    { 
                        git url: 'https://github.com/deepakpokhriyal/cvat-test.git', branch: 'dev'
                          sh  echo "Building in ${env.BRANCH_NAME}"
                //        sh "docker-compose -f docker-compose.yml -f docker-compose.dev.yml build"
                    }
                    
                }
            }
      
        }
    }
}
