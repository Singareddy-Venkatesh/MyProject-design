pipeline {
    agent any
    stages{
        stage('clone'){
            steps{
                git branch: 'DEV', url: 'https://github.com/Venna12/raviLogin.git'
            }
        }
        stage('validate'){
            steps{
                sh 'mvn validate '
            }
        }
        stage('compile'){
            steps{
                sh 'mvn compile'
            }
        }
        stage('test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }
        }
        stage('deploy to tomcat'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'Vcube', path: '', url: 'http://3.85.204.49:8080')], contextPath: null, war: '**/*.war'
            }   
        }
    }
}
