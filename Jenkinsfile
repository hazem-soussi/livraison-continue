pipeline {
  agent any
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            url: 'https://github.com/hazem-soussi/livraison-continue']]])
                }
            }
        }
        stage('Install') {
             steps{
                script{
                    sh "sudo npm install"
                }
            }
        }
        stage('Build') {
             steps{
                script{
                    sh "sudo ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
                }
            }
        }
        stage('Docker') {
             steps{
                script{
                    sh "sudo ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"
                }
            }
        }
        stage('DockerHub push') {
             steps{
                script{
                    sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml"
                }
            }
        }
       }
      }
