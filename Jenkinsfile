pipeline {
    agent any
    
    parameters {
        string(name: "USER_NAME", defaultValue: "mahad")
        string(name: "IMAGE_1",  defaultValue: "node")
        string(name: "NODE_IMAGE_VERSION", defaultValue: "18")
    }
    
    stages {
        stage('Run Node container') {
            steps {
                sh """
                    docker container run --name node_container --rm -d ${params.IMAGE_1}:${params.NODE_IMAGE_VERSION}
                    echo ${params.NODE_IMAGE_VERSION} ${params.USER_NAME}
                """
            }
        }
       
    }
}