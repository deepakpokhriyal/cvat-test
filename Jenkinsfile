pipeline {
    agent { label 'Master' }

    stages {
        stage('clone') {
            steps {
                sh 'echo #############  Cloning to Master Server ################'
                sh 'hostname'
            }
        }
        stage('build') {
            agent {
                        label "vagrant"
                    }
            steps {
                sh 'echo ########### BUILD ##############'
                sh 'pwd'
                sh 'hostname'
                sh 'sudo usermod -aG docker ${USER}'
                sh 'export DOCKER_HOST=127.0.0.1'
                sh 'sudo systemctl restart docker'
                sh 'sudo docker-compose -f docker-compose.yml -f docker-compose.dev.yml -f components/analytics/docker-compose.analytics.yml build'
            }
        }
       
        stage('Deploy') {
             
            steps {
                script {
                    if (env.BRANCH_NAME == 'master') {
                        echo 'I only execute on the master branch'
                        sh 'hostname'
                       
                    } else {
                        echo 'I execute elsewhere'
                    }
                }
            }
        }
    }
}
