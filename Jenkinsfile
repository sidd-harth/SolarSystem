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
                 sh 'docker push siddharth67/ss:""$GIT_COMMIT""'
               }
            }
        } 
    stage('Git Clone') {
            steps {
             
                 sh 'git clone https://github.com/sidd-harth/test-cd'
            
              dir("jenkins-demo") {
      
                sh 'sed -i "x#siddharth67.*#siddharth67/ss:""$GIT_COMMIT""#y" deployment.yaml'
                sh "git commit -am 'Publish new version' && git push || echo 'no changes'"
              }
            }
        } 
    }
}
