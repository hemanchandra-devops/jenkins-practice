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
        timeout(time: 10, unit: 'MINUTES') 
        disableConcurrentBuilds()
    }
     parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages {
        stage('Build') {
            steps {
                echo "Building"
                echo "$Course"
                // sleep 15
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.DEPLOY}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
            }
        }
        stage('Test') {
            steps {
                echo "Testing"
            }
        }
        stage('Deploy') {
            //  input {
            //     message "Should we continue?"
            //     ok "Yes, we should."
            //     submitter "alice,bob"
            //     parameters {
            //         string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
            //     }
            // }
            when {
                expression { ${params.DEPLOY} == "true" }
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