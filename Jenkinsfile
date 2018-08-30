pipeline {
    agent any
    stages {
        stage("Init") {
            steps {
                echo "Initializing"
                apt install virtualenv
            }
        }

        stage("build ansible") {
            steps {
                git credentialsId: 'JenkinsToken', url: 'https://github.com/lihopentium/playbook.exercise.git'
                virtualenv venv
                . venv/bin/activate
                sh "pip install -r requirements.txt"
                dir("exercise2") {
                    sh "ansible-playbook BuildAndRunContainer.yml -i inventory"
                }
            }
        }

    }
}
