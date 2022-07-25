pipeline {
  agent any

  stages {
      stage('Build Image') {
            steps {
                  sh 'docker build -t siddharth67/sol:""$GIT_COMMIT"" .'
             
            }
        }   
    }
}
