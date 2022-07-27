def myDir = '/tmp/cvat_installation_dir'

pipeline {
    agent any
    stages {
      stage('Build') {
            steps {
                git url: 'https://github.com/deepakpokhriyal/cvat-test.git', branch: 'master'
                sh "docker-compose -f docker-compose.yml -f docker-compose.dev.yml build"
            }
        }

      stage('Test') {
            steps {
                script {
                    sh "echo Testing...."
                }
            }
        }

     stage('Deploy') {
            steps {
            echo "Deploy.."
                sh  "docker-compose down"
                sh  "docker rm -f '\$(docker ps -aq | grep -v bitbucket)'"
                sh "cd /var/lib/jenkins/cvat_data/cvat-dev/ && docker-compose up -d"
            }
        }
    }
}
