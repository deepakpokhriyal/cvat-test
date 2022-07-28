pipeline {
    environment {
     BRANCH_NAME = "${GIT_BRANCH.split("/")[1]}"
     DEV_IP = "$(
  }
    agent any
    stages {
       stage('Build') {
            steps {
               script {
                    if (env.BRANCH_NAME == 'master') 
                    {
                        sh '''#!/bin/bash
                        echo 'Building in ${env.BRANCH_NAME}'
                         '''
           
                    } 
                    if (env.BRANCH_NAME == 'dev') 
                    {  
                        echo 'Building in ${env.BRANCH_NAME}'
                        git url: 'https://github.com/deepakpokhriyal/cvat-test.git', branch: 'dev'
                        sh "tar -cvz cvat.tar.gz * ; ls -lrth"
                        sh "scp -r cvat.tar.gz ${DEV_IP}:/tmp/"
                     
                         
                //        sh "docker-compose -f docker-compose.yml -f docker-compose.dev.yml build"
                    }
                    
                }
            }
      
        }
        
        stage('Deploy') {
            steps {
               script {
                   echo "helo"

                }
            }
      
        }
    }
}
