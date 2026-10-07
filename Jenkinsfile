pipeline {
    agent {
        label 'AGENT-1'
    }

    environment {
        COURSE = 'jenkins'
    }

    stages {

        stage('Build') {
            steps {
                echo 'Building...'

                sh '''
                    echo "Hello Build"
                    echo "Course: $COURSE"
                '''

                echo 'Building the application'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                echo 'Testing the application'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
                echo 'Deploying the application'
            }
        }
    }

    post {
        always {
            echo 'I will always say Hello again!'
            deleteDir()
        }

        success {
            echo 'Hello Success'
        }

        failure {
            echo 'Hello Failure'
        }
    }
}
