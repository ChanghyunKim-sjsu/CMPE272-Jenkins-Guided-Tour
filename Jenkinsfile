pipeline {
    agent none

    stages {
        stage('Java Environment') {
            agent {
                docker {
                    image 'maven:3.9.16-eclipse-temurin-21-alpine'
                }
            }
            steps {
                echo 'Running inside Maven + Java 21 container'
                sh 'mvn --version'
            }
        }

        stage('Node Environment') {
            agent {
                docker {
                    image 'node:24.21.0-alpine3.24'
                }
            }
            steps {
                echo 'Running inside Node.js container'
                sh 'node --version'
                sh 'node --eval "console.log(process.arch, process.platform)"'
            }
        }
    }
}
