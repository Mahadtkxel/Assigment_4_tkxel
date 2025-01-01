pipeline {
    agent any
    
    parameters {
        string(name: "BRANCH_NAME", defaultValue: "main")
        string(name: "GIT_URL", defaultValue: "")
        string(name: "TOOL_NAME", defaultValue: "")
    }
    
    stages {
        stage('Checkout Code') {
            steps {
                git branch: params.BRANCH_NAME, url: params.GIT_URL
            }
        }
       
    }
}