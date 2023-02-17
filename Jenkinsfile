pipeline {  
  agent any 
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))   
  }
  stages {
    stage('Build Image Backend') {
        steps {
            script{
                if (env.BRANCH_NAME == 'staging') {
                    dir('backend'){
                        sh 'docker build -t ramses01/cilist-backend:0.0.$BUILD_NUMBER-staging .'
                    }
                }
                else if (env.BRANCH_NAME == 'master') {
                    dir('backend'){
                         sh 'docker build -t ramses01/cilist-backend:0.0.$BUILD_NUMBER-master .' 
                    }
                }
                else {
                     sh 'echo Nothing to Build'
                }
            }
        }
    }
    stage('Push to Registry Backend') {
        steps {
            script {
             if (env.BRANCH_NAME == 'staging') {
            sh 'docker push ramses01/cilist-backend:0.0.$BUILD_NUMBER-staging'
                }
                else if (env.BRANCH_NAME == 'master') {
            sh 'docker push ramses01/cilist-backend:0.0.$BUILD_NUMBER-master' 
                }
                else {
                    sh 'echo Nothing to Push'
                }
        }
      }
    } 
  }       
}


