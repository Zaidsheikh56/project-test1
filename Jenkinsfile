pipeline {
  agent {
    label "slave-node"
  }
  environment {
    SONAR_TOKEN = credentials('Sonarpass')
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
        sudo yum update -y && yum install maven -y
        sudo mvn clean install
        '''
      }
    }
    stage ('Static Code Analysis') {
      steps {
        sh 'sudo cd /var/lib/jenkins/workspace/project-test/target'
        sh 'sudo mvn sonar:sonar -Dsonar.login=$SONAR_TOKEN'
        
      }
    }
  }
}
        
        
        
          
