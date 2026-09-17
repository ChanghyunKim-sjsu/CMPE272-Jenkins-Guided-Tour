pipeline {
    agent {
        docker {
            image 'maven:3.9.16-eclipse-temurin-21-alpine'
        }
    }

    environment {
        APP_NAME = 'CMPE272-Jenkins-Demo'
        COURSE = 'CMPE272'
    }

    stages {
        stage('Build') {
            steps {
                echo "Building ${APP_NAME}"

                sh '''
                    mkdir -p build
                    echo "Application package for $APP_NAME" > build/application.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'test -f build/application.txt'
                echo 'Tests passed!'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'

                sh '''
                    mkdir -p deployment
                    cp build/application.txt deployment/application.txt

                    echo "Deployed $APP_NAME successfully"
                    echo "Deployment environment: staging"
                    ls -lah deployment/
                '''
            }
        }
    }

    post {
        success {
            echo 'Build, Test, and Deploy completed successfully!'
        }

        failure {
            echo 'Pipeline failed before deployment completed.'
        }
    }
}
