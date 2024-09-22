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
    stage ('build stage') {
      step {
        sh'''
        sudo yum install dokcer -y
        sudo systemctl enable --now docker 
        sudo docker login -u zaidsheikh5656 -p zaidzimad12345
        sudo docker build -t zaissheikh5656/image56 .
        sudo docker push zaissheikh5656/image56
        '''
      }
    }
  }
}
  

        
        
        
          
