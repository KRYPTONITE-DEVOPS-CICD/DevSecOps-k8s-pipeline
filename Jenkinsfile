pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' //so that they can be downloaded later
            }
        }   
/*
      stage('SAST SonarQube') {
            steps {
              sh """mvn clean verify sonar:sonar -Dsonar.projectKey=numeric-devsecops -Dsonar.projectName='numeric-devsecops' -Dsonar.host.url=http://44.197.238.247:9000 -Dsonar.token=sqp_d8d896b845af48e0eefe00935407996d04e9edc2"""
            }
        }     
*/
      stage('TRIVY Vulnerability Scan - Docker') {
        steps {
              sh "bash trivy-docker-image-scan.sh"
          }          
        }
    
    }
}

