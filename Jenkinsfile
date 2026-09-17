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
        stage('Test') {
            steps {
                echo 'Creating test results...'

                sh '''
                    mkdir -p build/reports

                    cat > build/reports/test-results.xml <<'EOF'
<?xml version="1.0" encoding="UTF-8"?>
<testsuite name="CMPE272Demo"
           tests="2"
           failures="0"
           errors="0"
           skipped="0">
    <testcase classname="DemoTest" name="testPipeline"/>
    <testcase classname="DemoTest" name="testEnvironment"/>
</testsuite>
EOF
                '''
            }
        }

        stage('Build Artifact') {
            steps {
                echo 'Creating build artifact...'

                sh '''
                    mkdir -p build/libs
                    echo "Application: $APP_NAME" > build/libs/build-info.txt
                    echo "Course: $COURSE" >> build/libs/build-info.txt
                    echo "Build Number: $BUILD_NUMBER" >> build/libs/build-info.txt

                    cat build/libs/build-info.txt
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'build/libs/**/*',
                             fingerprint: true

            junit 'build/reports/**/*.xml'
        }
    }
}
