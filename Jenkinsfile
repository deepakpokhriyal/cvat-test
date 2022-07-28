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
                       echo 'Building in ${env.BRANCH_NAME}' 
                       sh "/var/lib/jenkins/scripts/build.sh 192.168.56.77 ${env.BRANCH_NAME} " 
           
                    } 
                    if (env.BRANCH_NAME == 'dev') 
                    {  
                        echo 'Building in ${env.BRANCH_NAME}'
                        sh "./var/lib/jenkins/scripts/build.sh 192.168.56.78 ${env.BRANCH_NAME} " 
 
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
