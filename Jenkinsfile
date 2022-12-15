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
                sh 'pwd'
                sh 'hostname'
                sh 'ip a'
                
            }
        }
        stage('Deploy') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'master') {
                        echo 'I only execute on the master branch'
                        sh 'docker-compose up -d'
                    } else {
                        echo 'I execute elsewhere'
                    }
                }
            }
        }
    }
}
