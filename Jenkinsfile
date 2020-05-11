pipeline {
  agent any 
  tools {
    maven 'M2_HOME'
  }
  stages {
    stage ('Initialize-Maven') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
      }
    }  
    stage ('Build-DBsql-File') {
      steps {
      sh 'mvn clean package'
       }
    }
      stage ('Deploy-To-DBserver') {
            steps {
           sshagent(['DBserver']) {
                sh 'scp -o StrictHostKeyChecking=no target/*.* ec2-user@100.26.97.114:/home/ec2-user/stage/Db.sql'
              }      
           }       
   } 
    
  }
}
