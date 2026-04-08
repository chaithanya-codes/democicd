pipeline {
    agent any

    environment {
        APP_NAME = "DemoApp"
    }

    parameters {
        string(name: 'ENV', defaultValue: 'dev', description: 'Environment')
    }

    stages {

        stage('Clone') {
            steps {
                echo "Cloning repo....."
                git 'https://github.com/chaithanya-codes/democicd.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building ${APP_NAME}"
                sh 'chmod +x app.sh'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'echo Tests Passed'
            }
        }

        stage('Parallel Checks') {
            parallel {
                stage('Lint') {
                    steps {
                        sh 'echo Linting...'
                    }
                }
                stage('Security Scan') {
                    steps {
                        sh 'echo Security scan...'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to ${params.ENV}"
                sh 'echo Deployment done'
            }
        }
    }

    post {
        success {
            echo "Pipeline Success ✅"
        }
        failure {
            echo "Pipeline Failed ❌"
        }
    }
}