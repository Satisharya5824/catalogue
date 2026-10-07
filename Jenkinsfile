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
                    def packageJson = new groovy.json.JsonSlurperClassic().parseText(
                        readFile('package.json')
                    )

                    appVersion = packageJson.version

                    echo "Package name: ${packageJson.name}"
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
