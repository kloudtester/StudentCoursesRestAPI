pipeline {
    agent { label 'agent'}
    triggers {
        pollSCM('* * * * *')
    }
    stages{
        stage('vcs'){
            steps{
                git url: 'https://github.com/kloudtester/StudentCoursesRestAPI.git',
                    branch: 'sprint_1'
            }
        }
        stage('docker'){
            steps{
                sh """sudo chmod 666 /var/run/docker.sock
                      docker image build -t krishnatester/spc:1.0 .
                      docker image push krishnatester/spc:1.0"""
            }
        }

    }
}