pipeline {
    agent any
    
    parameters {
        string(name: "USER_NAME", defaultValue: "mahad")
        string(name: "IMAGE_1",  defaultValue: "node")
        string(name: "IMAGE_1_TAG", defaultValue: "18-alpine")
        string(name: "IMAGE_2",  defaultValue: "maven")
        string(name: "IMAGE_2_TAG", defaultValue: "maven:3.3-jdk-17")
    }
    
    stages {
        stage("Run Node container") {
            steps {
                sh """
                    docker container run --name node_container --rm -d ${params.IMAGE_1}:${params.IMAGE_1_TAG}
                    echo ${params.IMAGE_1}:${params.IMAGE_1_TAG} ${params.USER_NAME}
                """
            }
        }

        stage("Run Maven container") {
            steps {
                sh """
                    docker run --rm --name my-maven-project -v "\$(pwd)":/usr/src/mymaven -w /usr/src/mymaven ${params.IMAGE_2}:${params.IMAGE_2_TAG}  mvn verify
                    echo ${params.IMAGE_2}:${params.IMAGE_2_TAG} ${params.USER_NAME}
                """
            }
        }

        // check
       
    }
}