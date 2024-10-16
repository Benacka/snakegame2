pipeline {
  agent none

  stages
}
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
    stage('SCA-SAST-SNYK-TEST')
    {
    agent
      {
        label 'ubuntu-Appserverver-2'
      }  
      steps
      {
        echo "SNYK-TEST"
      }

    stage('BUILD-AND-TAG')
    {
    agent
      {
        label 'ubuntu-Appserver-2'
      } 
    steps
    {
        script
        {
            def app = docker.build("Benacka/snakegame2")
            app.tag("latest")
        }
    }
    stage('POST-TO-DOCKERHUB')
    {
    agent
      {
        label 'ubuntu-Appserver-2'
      } 
    steps
    {
        script
        {
            docker.withRegistry("https://registry.hub.docker.com", "dockerhub_credentials")
            {
                def app = docker.image("Benacka/snakegame2")
                app.push("latest")
            }
        }
    }
  }

stage('DEPLOYMENT')
    {
    agent
      {
        label 'ubuntu-Appserver-2'
      }  
      steps
      {
        sh "docker-compose down"
        sh "docker-compose up -d"
      }
    }


}
