pipeline {
  agent any 
  stages {
      stage ('Deploy-To-DBserver') {
            steps {
           sshagent(['DBserver']) {
                sh 'scp -o StrictHostKeyChecking=no *.* ec2-user@100.26.97.114:/home/ec2-user/stage'
                sh 'ssh ec2-user@100.26.97.114 ". /home/ec2-user/.oracle_profile && cd /home/ec2-user/pycode && python3 /home/ec2-user/pycode/deploy.py"'
                }      
           }       
   } 
    
  }
}
