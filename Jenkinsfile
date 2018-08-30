pipeline {
    agent {
        docker {
            image 'python:alpine'
        }
    }
    stages {
        stage("build ansible") {
            steps {
                git credentialsId: 'JenkinsToken', url: 'https://github.com/lihopentium/playbook.exercise.git'
                sh "pip install -r requirements.txt"
                dir("exercise2") {
                    sh "ansible-playbook BuildAndRunContainer.yml -i inventory"
                }
            }
        }
    }
}
