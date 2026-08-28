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
                // sleep 15
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
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    post { 
        always { 
            echo 'I will always say Hello again!'
            cleanWs()
            // echo "Hello ${params.PERSON}"

            // echo "Biography: ${params.BIOGRAPHY}"

            // echo "Toggle: ${params.TOGGLE}"

            // echo "Choice: ${params.CHOICE}"

            // echo "Password: ${params.PASSWORD}"
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