pipeline {
  agent any
  environment {
    SONAR_URL = 'http://3.145.148.182:9000/'
  }
    
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
      steps {
        withCredentials([string(credentialsId: 'Sonarpass', variable: 'SONAR_TOKEN')]) {
                        sh """
                        echo "Running SonarQube analysis with token: $SONAR_TOKEN"   # $SONAR_TOKEN will be masked
                        sudo cd /var/lib/jenkins/workspace/Project-test/
                        mvn sonar:sonar -Dsonar.host.url=${SONAR_URL} -Dsonar.login=$SONAR_TOKEN
                        """
        }
        
      }
    }
  }
}
        
        
        
          
