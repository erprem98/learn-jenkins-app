pipeline {
    agent any
    
    tools {
        dockerTool 'my-docker' 
    }

    stages {
        stage('Docker Test') {
            steps {
                // Uses a tiny alpine image to print a success message and verify the docker version
                sh 'docker run --rm alpine sh -c "echo === DOCKER IS WORKING PERFECTLY === && uname -a"'
            }
        }
    }
}
