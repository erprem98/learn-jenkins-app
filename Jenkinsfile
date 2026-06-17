pipeline {
    agent any
    
    // 1. ADD THIS GLOBAL TOOLS BLOCK
    tools {
        dockerTool 'my-docker' 
    }
  
    stages {
       stage('Build') {
           agent {
               docker {
                   image 'node:18-alpine'
                   reuseNode true
               }
           }
           steps {
               sh '''
                   echo "=== Project Files ==="
                   ls -la
                   
                   echo "=== Environment Versions ==="
                   node --version
                   npm --version
                   
                   echo "=== Building Application ==="
                   
               '''
           }
       }
    }
}
