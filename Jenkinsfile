pipeline {
    agent any

    stages {
    
        stage('Build')
        {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                ls -la
                node --version
                npm --version
                npm ci
                npm run build
                ls -la
                '''
            }
        }
            stage('aws')
        {
            agent{
                docker{
                    image 'amazon/aws-cli'
                    args "--entrypoint=''"
                }
            }
            steps{
                withCredentials([usernamePassword(credentialsId: 'aws -cred', passwordVariable: 'AWS_SECRET_ACCESS_KEY', usernameVariable: 'AWS_ACCESS_KEY_ID')]) {
                sh '''
                aws --version
                echo "Hi" > index.html
                aws s3 cp index.html s3://jenkins-app23433/index.html
                aws s3 sync . s3://jenkins-app23433
                 
                '''}
            
            }
        }
        stage('Test')
        {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
            sh '''
            test -f build/index.html
            npm test
            '''
            }
       }
        //   stage('Deploy') 
        // {
        //     agent {
        //         docker {
        //             image 'node:18-alpine'
        //             reuseNode true
        //         }
        //     }
        //     steps {
        //         sh '''
        //         npm install netlify-cli -g
        //         netlify --version 
               
        //         '''
        //     }
        // }
        
    }
}
