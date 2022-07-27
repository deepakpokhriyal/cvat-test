pipeline {
    agent any

    environment {
        DISABLE_AUTH = 'true'
        BRANCH_NAME = "${GIT_BRANCH.split("/")[1]}"
    }

    stages {
        stage('Build') {
            steps {
   #           sh "echo ${BRANCH_NAME}"
            }
        }
    }
}
