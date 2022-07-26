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
               // sh 'git remote set-url  origin git@github.com:sidd-harth/test-cd.git'
               // sh "git commit -am 'Publish new version' && git push origin main || echo 'no changes'"
                sh 'gh auth status'
                sh 'gh auth login -h github.com  -p https --with-token < /home/devsecops/token.txt'
                
                sh 'gh auth status'
              }
            }
        } 
    }
}
