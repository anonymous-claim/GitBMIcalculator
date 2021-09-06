pipeline {

    agent {
        node {
            label 'master'
        }
    }

    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '16', 
                    numToKeepStr: '10'
            )
    }

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }

        stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/feature']], 
                    userRemoteConfigs: [[url: 'https://github.com/anonymous-claim/GitBMIcalculator.git']]
                ])
            }
        }

        stage('Testing Stage') {
            steps {
                sh """
                echo "Running Tests"
                """
            }
        }

        stage('Deploy Stage') {
            steps {
                checkout([
                   $class: 'GitSCM', 
                    branches: [[name: '*/feature']],
                    userRemoteConfigs: [[url: 'https://github.com/anonymous-claim/GitBMIcalculator.git']]
                    ])
                    sh """
                    echo "Deploying + branches"
                """
                
            }
        }
    }   
}
