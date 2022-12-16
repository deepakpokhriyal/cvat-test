pipeline {
    agent { label 'Master' }

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
                
            }
        }
       
        stage('Deploy') {
            steps {
                node(label 'vagrnat')
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
