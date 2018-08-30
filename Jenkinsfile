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
                githubPRComment comment: githubPRMessage('DAMN GREAT'), statusVerifier: allowRunOnStatus('SUCCESS')

            }
        }

    }
   
}
