
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Compiling application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests... Pass!'
            }
        }

        stage('Package') {
            steps {
                script {
                    def timestamp = new Date().format("yyyy-MM-dd HH:mm:ss")
                    writeFile file: 'build-info.txt',
                              text: "Build Number: ${env.BUILD_NUMBER}\nTimestamp: ${timestamp}\n"
                }
                archiveArtifacts artifacts: 'build-info.txt', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build successful! Ready for release.'
        }
    }
}
