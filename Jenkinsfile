pipeline {
    agent any
    
    tools {
        dockerTool 'my-docker' 
    }

    stages {
        stage('Build') {
            steps {
                // We use your working 'sh' method, but map the volume so npm cache and workspace persist
                sh 'docker run --rm -v /var/jenkins_home/workspace/Jenkins-app:/app -w /app node:18-alpine sh -c "npm ci && npm run build"'
            }
        }
    }
}
