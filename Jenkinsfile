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
                sh 'docker image build -t krishnatester/spc:1.0 .'
                sh 'docker scan krishnatester/spc:1.0'
                sh 'docker image push krishnatester/spc:1.0'
            }
        }
        
    }
}