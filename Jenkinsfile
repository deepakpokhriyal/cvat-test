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
                sh 'docker-compose -f docker-compose.yml -f components/analytics/docker-compose.analytics.yml up -d --build'
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
