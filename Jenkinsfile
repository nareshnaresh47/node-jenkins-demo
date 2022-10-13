pipeline {
    agent any
    stages {
        stage('Tests') {
            steps {
//                 script {
//                    docker.image('node:10-stretch').inside { c ->
                        echo 'Building..'
                        sh 'npm install'
                        echo 'Testing..'
                        sh 'npm test'
//                         sh "docker logs ${c.id}"
//                    }
//                 }
            }
        }
        stage('Build and push docker image') {
            steps {
                script {

                  
                    sh 'docker build -t nodedemo .' 
                    }
                }
            }
        }
        stage('Deploy to remote docker host') {
          
            steps {
                script {

      
                   sh 'docker run -d --name node-demo -p 80:3000 nodedemo'
                }
            }
        }
    }
}
