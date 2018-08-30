//Pass Status back to GitHub based on Trigger Type.
def setBuildStatus(String message, String state, String repo_url, String job_name, String commit_sha) {
    retry(3){
        step([
            $class: "GitHubCommitStatusSetter",
            reposSource: [$class: "ManuallyEnteredRepositorySource", url: repo_url],
            contextSource: [$class: "ManuallyEnteredCommitContextSource", context: job_name],
            errorHandlers: [[$class: "ChangingBuildStatusErrorHandler", result: state]],
            commitShaSource: [$class: "ManuallyEnteredShaSource", sha: commit_sha],
            statusBackrefSource: [$class: "ManuallyEnteredBackrefSource", backref: "${BUILD_URL}display/redirect"],
            statusResultSource: [$class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
        ]);
    }
} 

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
                sendBuildStatus("Damn Great", "SUCCESS", "https://github.com/jhowliu2018/demo", "${JOB_BASE_NAME}", "${GITHUB_PR_HEAD_SHA}")
            }
        }

    }
   
}
