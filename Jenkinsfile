pipeline {
    agent {
        node {
            label 'agent-1'
        }
    }
    environment {
        REGION = 'us-east-1'
        PROJECT = 'roboshop'
    }
    parameters {
        string(name: 'appVersion', description: 'Which app version you want to deploy')
        choice(name: 'deploy_to', choices: ['dev', 'qa', 'prod'], description: 'Pick something')
    }
    stages {
        stage ('Deploy Job') {
            steps {
                script {
                    sh '''
                        #!/bin/bash
                        echo "Triggering Deploy Job ..."
                        aws update-kubeconfig --region ${REGION} --name ${PROJECT}-${params.deploy_to}

                    '''
                
                }
            }
        }
    }
}