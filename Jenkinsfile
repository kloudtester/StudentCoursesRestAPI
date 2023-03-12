pipeline {
    agent { label 'agent'}
    triggers {
        pollSCM('* * * * *')
    }
    stages{
        stage('vcs'){
            steps{
                git url: 'https://github.com/kloudtester/StudentCoursesRestAPI.git',
                    branch: 'dev'
            }
        }
        stage('docker'){
            steps{
                sh """sudo chmod 666 /var/run/docker.sock
                      docker image build -t krishnatester/spc:1.0 .
                      docker scan krishnatester/spc:1.0
                      docker image push krishnatester/spc:1.0"""
            }
        }

    }
}