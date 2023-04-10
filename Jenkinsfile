pipeline {
    agent any
    tools{
        maven 'maven 3.6.3'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/nayabshaik0532/Dev-auto.git']])
                sh 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t javatechie/devops-integration .'
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                   {
                   sh 'docker login -u nayabshaik0587 -p n@yab80994980'

}
                   sh 'docker push javatechie/devops-integration'
                }
            }
        }
        
    }
}
