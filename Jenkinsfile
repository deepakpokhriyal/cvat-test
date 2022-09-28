pipeline {
    agent any

    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }

    stages {
        stage('BranchCheck') {
       
              if (env.BRANCH_NAME == 'master') {
              echo 'Hello from main branch'
              } else {
              sh "echo 'Hello from ${env.BRANCH_NAME} branch!'"
               }
               // sh 'printenv'
            
        }
    }
}
