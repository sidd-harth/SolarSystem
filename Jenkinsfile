pipeline {
  agent any

  stages {
//       stage('Build Image') {
//             steps {
//                   sh 'sudo docker build -t siddharth67/ss:""$GIT_COMMIT"" .'
             
//             }
//         } 
    
//     stage('Push Image') {
//             steps {
//               withDockerRegistry([credentialsId: "docker-hub", url: ""]) {
//                  sh 'docker push siddharth67/ss:""$GIT_COMMIT""'
//                }
//             }
//         } 
    
    
//     stage('Git Clone') {
//             steps {
             
//                // sh 'git clone -b feature https://github.com/sidd-harth/test-cd'
            
//               dir("test-cd/jenkins-demo") {
//                 sh "git config --global user.email 'ci@ci.com'"
//                 sh 'sed -i "s#siddharth67.*#siddharth67/ss:""$GIT_COMMIT""#g" deployment.yaml'
//                 sh 'cat deployment.yaml'
//                // sh 'git remote add origin https://sidd-harth:&6ytrewQ@github.com/sidd-harth/test-cd.git'
//                sh 'git commit -am "Publish new version"'
//                sh 'git push origin feature'
//               //  sh 'gh auth status'
//                sh 'gh auth login -h github.com  -p https --with-token < /home/devsecops/token.txt'
                
//                 sh 'gh auth status'
//               sh 'gh pr create -a @me --title test1 --body wiilThisWork -B main'
//               }
//             }
//         } 
    stage('Git Clone') {
       when { expression { return fileExists ('test-cd') } }
        steps {
               echo "file exists"
              }
    }
     stage('Update Manifest') {
      
        steps {
                 sh "git config --global user.email 'ci@ci.com'"
                sh 'sed -i "s#siddharth67.*#siddharth67/ss:""$GIT_COMMIT""#g" deployment.yaml'
                sh 'cat deployment.yaml'
           sh 'git commit -am "Publish new version""$GIT_COMMIT"""'
               sh 'git push origin feature'
              }
    }
    
     stage('Raisse PR') {
      
        steps {
    sh 'gh auth login -h github.com  -p https --with-token < /home/devsecops/token.txt'
                
                sh 'gh auth status'
              sh 'gh pr create -a @me --title test1 --body wiilThisWork -B main'
        }}
    }
}
