pipeline {
  agent any
  stages {
    stage('git checkout') {
          steps{
            git branch: 'main', url: 'https://github.com/iam-veeramalla/Jenkins-Zero-To-Hero.git'
          }
    }
    stage('Build Stage') {
            steps{ 
              sh' sudo yum install maven -y && sudo cd java-maven-sonar-argocd-helm-k8s/spring-boot-app/ && mvn clean install'
            }
    }

  }
}
