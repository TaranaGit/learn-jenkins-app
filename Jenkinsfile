pipeline {
    agent any

    stages {
        stage('Hello') {
            agent{
                docker{
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
            //    echo 'Hello world'
            }
        }

        stage('Test'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps{
                sh '''
                    npm test
                '''
               
            }
        }
 
            stage('Deploy') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    npm install -g netlify-cli
                    netlify --version
                '''
            //    echo 'Hello world'
            }
        }
   }

}
