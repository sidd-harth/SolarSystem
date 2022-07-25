pipeline {
  agent any

  stages {
      stage('Build Image') {
            steps {
                  sh 'sudo docker build -t siddharth67/sol:""$GIT_COMMIT"" .'
             
            }
        }   
    }
}
