pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment { 
        Course = 'Jenkins'
    }
    options {
        timeout(time: 10, unit: 'SECONDS') 
        disableConcurrentBuilds()
    }
    stages {
        stage('Build') {
            steps {
                echo "Building"
                echo "$Course"
                sleep 15
            }
        }
        stage('Test') {
            steps {
                echo "Testing"
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying"
            }
        }
    }

    post { 
        always { 
            echo 'I will always say Hello again!'
            cleanWs()
        }
        success {
            echo 'I will run if pipeline sucess'
        }
        failure {
            echo 'I will run if pipeline failed'
        }
        aborted {
            echo 'pipeline is aborted'
        }
    }
}