pipeline{
    agent any

    stages{
        stage ("Clean WS"){
            steps{
                cleanWs()
            }
        }

        stage ("git checkout"){
            steps{
            script{
                git branch: 'REL-001', url: 'https://github.com/Sukhanth-9821/CodeExperts_CI.git'
            }
            }
        }

        stage ("Docker Build"){
            steps{
                script{
                    def dockerHome = tool name: "dockertool", type: "dockerTool"

                    env.PATH = "${dockerHome}/bin:${env.PATH}"

                    imagename = "localhost:8085/codeexperts:${env.BUILD_NUMBER}"
                    sh """
                    docker build -t ${imagename} .
                    docker images

                    """
                }
            }
        }

    }
}