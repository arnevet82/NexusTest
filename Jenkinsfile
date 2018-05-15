pipeline {
environment {
     name = 'jenkinsTestHelloWorld'
     }

    agent any
    stages {
        stage('build') {
            steps {
                 echo 'building...'
                 checkout scm
                 
            }
        }
  stage('run'){
            steps {
                sh 'python --version'
                sh 'python python_test.py'
                sh 'curl -v -u admin:admin123 --upload-file /home/nexus/hello_world_test/python_test.py http://nexus:8081/repository/git-products/'
            }
        }
    }
}
