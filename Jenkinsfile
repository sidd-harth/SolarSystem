pipeline {
  agent any

  environment {
    GIT_TOKEN = credentials('github-token')
  }

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

    stage('Clone Repo') {
      steps {
        script {
          if (fileExists('test-cd')) {

            echo 'Cloned repo already exists - Pulling latest changes'

            dir("test-cd") {
              sh 'git pull'
            }

          } else {
            sh 'git clone -b feature https://github.com/sidd-harth/test-cd.git'
          }
        }
      }
    }
    stage('Update Manifest') {

      steps {
        dir("test-cd/jenkins-demo") {
          sh "git config --global user.email 'ci@ci.com'"
          sh 'sed -i "s#siddharth67.*#siddharth67/ss:""$GIT_COMMIT""#g" deployment.yaml'
          sh 'cat deployment.yaml'
        }
      }
    }

    stage('Commit & Push') {

      steps {
        dir("test-cd/jenkins-demo") {
          sh 'git remote set-url origin https://$GIT_TOKEN@github.com/sidd-harth/test-cd.git'
          sh 'git checkout feature'
          sh 'git add -A'
          sh 'git commit -am "Updated new image version for GIT COMMIT - ""$GIT_COMMIT"""'
          sh 'git push origin feature'
        }
      }
    }

    stage('Raise PR') {

      steps {
        dir("test-cd/jenkins-demo") {
          sh 'gh auth login -h github.com  -p https --with-token < /home/devsecops/token.txt'
          sh 'gh auth status'
          sh 'gh pr create -a @me --title "Updated Image Version" --body "Updated Solar System - ""$GIT_COMMIT"""  -B main'
        }
      }
    }
  }
}
