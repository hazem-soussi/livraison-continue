pipeline {
  agent any
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            url: 'https://github.com/aminegongi/cd_lab1']]])
                }
            }
        }
        #stage('Install') {
        #     steps{
        #        script{
        #            sh "npm install"
        #        }
        #    }
        #}
        #stage('Build') {
        #     steps{
        #        script{
        #            sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
        #        }
        #    }
        #}
        stage('Docker') {
             steps{
                script{
                    sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"
                }
            }
        }
       }
      }
