pipeline {
    agent any
    stages {
        stage("Init") {
            steps {
                echo "Initializing"
            }
        }
        stage("build") {
            steps {
                echo "buidlddd"
            }
        }

    }
    post {
        success {
            githubPRComment comment: githubPRMessage('Build ${BUILD_NUMBER} ${BUILD_STATUS}'), statusVerifier: allowRunOnStatus('SUCCESS')   
        }
    }
}
