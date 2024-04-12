@Library('my-shared-library') _

pipeline{

    agent any
    //agent { label 'Demo' }

    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
        string(name: 'ImageName', description: "name of the docker build", defaultValue: 'javapp')
        string(name: 'ImageTag', description: "tag of the docker build", defaultValue: 'v1')
        string(name: 'DockerHubUser', description: "name of the Application", defaultValue: 'praveensingam1994')
    }

    stages{
         
        stage('Git Checkout'){
                    when { expression {  params.action == 'create' } }
            steps{
              log.info 'git checkout'
            }
        }
         stage('Unit Test maven'){
         
         when { expression {  params.action == 'create' } }
            steps{
              log.info 'Starting maven unit test'
            }
        }
         stage('Integration Test maven'){
         when { expression {  params.action == 'create' } }
            steps{
              log.info 'starting maven integeration testing'
            }
        }
        stage('Static code analysis: Sonarqube'){
         when { expression {  params.action == 'create' } }
            steps{
              log.info 'starting sonarqube'
              
            }
       }
       stage('Quality Gate Status Check : Sonarqube'){
         when { expression {  params.action == 'create' } }
            steps{
                  log.info 'sonarqube quality gate check'
            }
       }
        stage('Maven Build : maven'){
         when { expression {  params.action == 'create' } }
            steps{
              log.info 'starting maven build'
            }
        }
        stage('Docker Image Build'){
         when { expression {  params.action == 'create' } }
            steps{
                log.info 'starting docker build'
            }
        }
         stage('Docker Image Scan: trivy '){
         when { expression {  params.action == 'create' } }
            steps{
              log.info 'starting scanning image'
            }
        }
        stage('Docker Image Push : DockerHub '){
         when { expression {  params.action == 'create' } }
            steps{
                log.info 'pushing docker image'
            }
        }   
        stage('Docker Image Cleanup : DockerHub '){
         when { expression {  params.action == 'create' } }
            steps{
              log.info 'starting cleaning docker image'
            }
        }      
    }
}
