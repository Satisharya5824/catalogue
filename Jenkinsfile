
pipeline {
    agent {
        label 'AGENT-1'
    }

    environment {
        appVersion = ''
    }

    stages {

        stage('Read package.json') {
            steps {
                script {
                    appVersion = sh(
                        script: "grep '\"version\"' package.json | head -1 | sed 's/.*\"version\": \"\\([^\"]*\\)\".*/\\1/'",
                        returnStdout: true
                    ).trim()

                    echo "Package version: ${appVersion}"
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the application'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying ${appVersion}"
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
