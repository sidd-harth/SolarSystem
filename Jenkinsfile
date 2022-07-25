pipeline {
  agent any

  stages {
      stage('Build Image') {
            steps {
                  sh 'sudo docker build -t siddharth67/ss:""$GIT_COMMIT"" .'
             
            }
        } 
    
    stage('Push Image') {
            steps {
                 sh "docker login --username siddharth67 --password Qwerty6& && docker push siddharth67/ss:""$GIT_COMMIT"""
             
            }
        } 
    }
}
