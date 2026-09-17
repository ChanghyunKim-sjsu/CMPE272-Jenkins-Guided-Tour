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
                    mkdir -p build/output
                    echo "Build completed for $APP_NAME" > build/output/result.txt
                    cat build/output/result.txt
                '''
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution has finished.'
            echo 'Cleaning up the workspace...'
            deleteDir()
        }

        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed.'
        }
    }
}
