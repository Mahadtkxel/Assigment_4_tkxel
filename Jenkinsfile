pipeline {
    agent any
    
    parameters {
        string(name: "USER_NAME", defaultValue: "mahad")
        string(name: "IMAGE_1",  defaultValue: "node")
        string(name: "IMAGE_1_TAG", defaultValue: "18-alpine")
        string(name: "IMAGE_2",  defaultValue: "maven")
        string(name: "IMAGE_2_TAG", defaultValue: "3-jdk-8-alpine")
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
                    docker run --rm -w /usr/src/mymaven ${params.IMAGE_2}:${params.IMAGE_2_TAG} mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-maven-docker-project -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
                    echo ${params.IMAGE_2}:${params.IMAGE_2_TAG} ${params.USER_NAME}
                """
            }
        }

        
       
    }
}