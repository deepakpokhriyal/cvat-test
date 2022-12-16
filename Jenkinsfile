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
               // sh 'sudo docker-compose -f docker-compose.yml -f docker-compose.dev.yml -f components/analytics/docker-compose.analytics.yml build'
            }
        }
       
        stage('Deploy') {
             
            steps {
                script {
                    if (env.BRANCH_NAME == 'master') {
                        echo 'I only execute on the master branch'
                        sh 'hostname'
                        sh 'helm upgrade -i cvat ./helm-chart -f ./helm-chart/values.yaml'
                       
                    } else {
                        echo 'I execute elsewhere'
                    }
                }
            }
        }
    }
}
