pipeline {
 agent any
 stages {
   stage('checkout') {
     steps {
       git(url: 'https://github.com/kshitizsh12/Simple.git', branch: 'master', changelog: true, credentialsId: '10sharma10', poll: true)
     }
   }
   stage('build') {
     options {
        timestamps {
          logstash {
            node('label1') {
              sh'''
                echo 'Hello, World!'
              '''
              try {
                // do something that fails
                sh "exit 1"
                currentBuild.result = 'SUCCESS'
              } catch (Exception err) {
                currentBuild.result = 'FAILURE'
              }
            }
          }
        }
     }

     steps {
       build 'new 1'
     }
   }
   stage('sonarqube') {
     steps {
       build 'new1 sonar'
     }
   }
   stage('gate') {
     steps {
       build 'new1gate'
     }
   }
 }
}


