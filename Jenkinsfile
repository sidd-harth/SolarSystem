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
             
             //    sh 'git clone https://github.com/sidd-harth/test-cd'
            
              dir("test-cd/jenkins-demo") {
                sh "git config --global user.email 'ci@ci.com'"
                sh 'sed -i "s#siddharth67.*#siddharth67/ss:""$GIT_COMMIT""#g" deployment.yaml'
                sh 'cat deployment.yaml'
                sh 'git remote set-url  origin https://github.com/sidd-harth/test-cd'
                sh "git commit -am 'Publish new version' && git push origin main || echo 'no changes'"
              }
            }
        } 
    }
}
