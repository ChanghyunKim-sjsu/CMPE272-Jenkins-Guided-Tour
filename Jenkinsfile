/* Requires the Docker Pipeline plugin */
pipeline {
    agent {
        docker {
            image 'maven:3.9.16-eclipse-temurin-21-alpine'
        }
    }

    stages {
        stage('build') {
            steps {
                sh 'echo "Hello World"'

                sh '''
                    echo "Running multiple shell steps"
                    pwd
                    ls -lah
                '''

                sh 'mvn --version'
            }
        }
    }
}
