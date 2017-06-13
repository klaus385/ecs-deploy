pipeline {
  agent { label "docker" }
  
  stages {
    stage('Build') {
      steps {
        script {
          docker.withRegistry('https://pwolfbees-docker.jfrog.io', 'artifactory') {
            sh "docker build -t ecsdeploy ."
          }
        }
      }
    }
     stage('Deploy') {
       steps {
         sh """
           docker tag ecsdeploy pwolfbees-docker.jfrog.io/pwolfbees/tools/ecsdeploy:latest
           docker push pwolfbees-docker.jfrog.io/pwolfbees/tools/ecsdeploy:latest
           """
       }
     }
  }
}
