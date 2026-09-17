pipeline {
    agent none

    environment {
        APP_NAME = 'CMPE272-Jenkins-Demo'
        COURSE = 'CMPE272'
    }

    stages {
        stage('Java Environment') {
            agent {
                docker {
                    image 'maven:3.9.16-eclipse-temurin-21-alpine'
                }
            }

            steps {
                echo "Application: ${APP_NAME}"
                echo "Course: ${COURSE}"

                sh '''
                    echo "APP_NAME from shell: $APP_NAME"
                    echo "COURSE from shell: $COURSE"
                    mvn --version
                '''
            }
        }

        stage('Node Environment') {
            agent {
                docker {
                    image 'node:24.21.0-alpine3.24'
                }
            }

            steps {
                echo "Running ${APP_NAME} inside Node.js container"
                sh 'node --version'
            }
        }
    }
}
