pipeline {
    agent any
    
    // 1. Force Jenkins to register 'my-docker' before any stage executes
    tools {
        dockerTool 'my-docker' 
    }

    stages {
       stage('Build') {
        //    agent {
        //        docker {
        //            image 'node:18-alpine'
        //            // 2. Shares the workspace between the host and the container
        //            reuseNode true
        //        }
        //    }
           steps {
               sh '''
                echo "Building the application..."
               '''
           }
       }
    }
}
