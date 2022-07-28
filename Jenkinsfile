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
                        sh '''#!/bin/bash
                        echo 'Building in ${env.BRANCH_NAME}'
                        BD="/tmp/created_by_jenkins/"
                        ssh vagrant@192.168.56.77 "
                        rm -rf "$BD"
                        mkdir "$BD"
                        git clone --branch $1 https://github.com/deepakpokhriyal/cvat-test.git "$BD"
                        cd "$BD" ; sudo docker-compose -f docker-compose.yml -f docker-compose.dev.yml build
                        exit"
    
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
