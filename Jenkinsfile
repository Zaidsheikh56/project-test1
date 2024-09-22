pipeline {
  agent any
    
  stages {
    stage('Git Checkout') {
      steps {
        git 'https://github.com/Pritam-Khergade/student-ui.git' 
      }
    }
    stage  ('BuildCode') {
      steps {
        sh'''
        sudo yum update -y &&  sudo yum install maven -y
        sudo mvn clean install
        '''
      }
    }
    stage ('Static Code Analysis') {
        environment {
        SONAR_URL = "http://3.14.146.27:9000"
      }
      steps {
        withCredentials([string(credentialsId: 'sonarqube', variable: 'SONAR_AUTH_TOKEN')]) {
          sh 'cd /var/lib/jenkin/workspace/Project-test && mvn sonar:sonar -Dsonar.login=$SONAR_AUTH_TOKEN -Dsonar.host.url=${SONAR_URL}'
        }
        
        }
        
      }
    }
  }

        
        
        
          
