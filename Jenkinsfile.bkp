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
                    withAWS(region:'us-east-1',credentials:'aws-auth') {
                        sh """
                            
                            echo "Triggering Deploy Job ..."
                            aws eks update-kubeconfig --region ${REGION} --name ${PROJECT}-${params.deploy_to}
                            kubectl get nodes

                        """
                    }                
                }
            }
        }
    }
}