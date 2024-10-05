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
              sh''' 
              sudo yum install maven -y 
              sudo -i 
              cd /var/lib/jenkins/workspace/project-test/java-maven-sonar-argocd-helm-k8s/spring-boot-app/
              mvn clean install
              '''
            }
    }
    stage('Static code Analysis') {
          environment {
              SONAR_URL = "http://18.218.214.100:9000"
          }
           steps{
             withCredentials([string(credentialsId: 'sonarqube', variable: 'SONAR_CRED')]) { 
                  sh'''
                  sudo -i
                  cd /var/lib/jenkins/workspace/project-test/java-maven-sonar-argocd-helm-k8s/spring-boot-app/
                  mvn sonar:sonar -Dsonar.login=$SONAR_CRED -Dsonar.host.url=${SONAR_URL}
                  '''
             }
           }
    }
    stage('Docker build') {
           steps{
             withCredentials([usernameColonPassword(credentialsId: 'docker-cred', variable: 'DOCKER_CRED')]) {
                  sh'''
                  sudo systemctl enable --now docker 
                  sudo docker build -t zaidsheikh5656/first-project .
                  sudo docker login
                  sudo docker push zaidsheikh5656/first-project
                  '''
             }
           }
                  
}
  }
}
          

        
