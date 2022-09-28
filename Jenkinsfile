pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                sh 'echo #############  CLONING ################'
            }
        }
        stage('build') {
            steps {
                sh 'echo ########### BUILD ##############'
                sh 'docker-compose -f docker-compose.yml -f docker-compose.https.yml build'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'master') {
                        echo 'I only execute on the master branch'
                    } else {
                        echo 'I execute elsewhere'
                    }
                }
            }
        }
    }
}
