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
              sh''' sudo yum install maven -y 
              sudo /var/lib/jenkins/workspace/project-test/java-maven-sonar-argocd-helm-k8s/spring-boot-app && sudo mvn clean install
              
            }
    }

  }
}
