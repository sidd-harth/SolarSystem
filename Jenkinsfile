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
               withDockerRegistry([credentialsId: "docker-hub", url: ""]) {
           
                 sh 'sudo docker push siddharth67/ss:""$GIT_COMMIT""'
               }
            }
        } 
    }
}
