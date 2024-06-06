#!/usr/bin.env groovy

pipeline {   
    agent any
    stages {
        stage("test") {
            steps {
                script {
                    echo "Testing the application..."

                }
            }
        }
        stage("build") {
            steps {
                script {
                    echo "Building the application..."
                }
            }
        }

        stage("deploy") {
            steps {
                script {
                    echo "Deploying the application..."
                    def dockerCmd = 'docker run -p 3080:3080 -d ccroberts1/demo-app:1.0'
                    sshagent(['ec2-server']) {
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@54.165.85.234 ${dockerCmd}"
                    }
                }
            }
        }               
    }
} 
