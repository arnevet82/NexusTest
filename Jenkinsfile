pipeline {
environment {
     name = 'jenkinsTestHelloWorld'
     }

    agent any
    stages {
        stage('build') {
            steps {
                 echo 'building...'
                 checkout([
            $class: 'GitSCM',
            branches: [[name: '*/master']], 
            extensions: [], 
            userRemoteConfigs: [[credentialsId: 'd6564d07-a13c-4477-a5e3-734017e4d590', url: 'https://github.com/arnevet82/NexusTest.git']]
                 ])
                 
            }
        }
         stage('upload to nexus registry') {
            steps {
                 sh 'curl -v -u admin:admin123 --upload-file hello.py http://nexus:18081/repository/git-products/'                 
            }
        }
       stage('run'){
                 steps {
                     sh 'python --version'
                     sh 'python python_test.py'
                 }
             }
         }
     }
