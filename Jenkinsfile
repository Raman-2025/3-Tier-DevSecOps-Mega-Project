pipeline{
 agent any
 stages{
  stage('code'){
    steps{ 
      git url:'', branch:'main'
   }
  }
  stage('build frontend'){
    steps{
     dir ('client'){
       sh ' docker build -t frontend:latest .'
    }
   } 
  }
  stage('build backend'){
    steps{
     dir ('api'){
       sh 'docker build -t backend:latest .'
    }
   }
  }
  stage('deploy'){
    steps{
      sh 'docker compose down && docker compose up -d --build'
   }
  }   
 }
}
