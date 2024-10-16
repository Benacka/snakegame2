pipeline {
  agent none

  stages
  {
    stage('CLONE GIT REPOSITORY')
    {
    agent
      {
        label 'ubuntu-Appserver-2'
      }  
      steps
      {
        checkout scm  
      }
    }
    
  }

}
