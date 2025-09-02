pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' //so that they can be downloaded later
            }
        }   

    stage('Docker Build and Push') {
        steps {
          withDockerRegistry([credentialsId: "docker-cred", url: ""]) {
            sh 'printenv'
            sh 'docker build -t biswajitt/numeric-app:latest .'
            sh 'docker push biswajitt/numeric-app:latest'
          }
        }
    }
    
    }
}

