pipeline {
 agent any
 stages {
    stage('checkout') {
      steps {
        git(url: 'https://github.com/kshitizsh12/Simple.git', branch: 'master', changelog: true, credentialsId: '10sharma10', poll: true)
       }
    }
    stage('build') {
      steps {
      logstash {
                node('master') {
                                build 'new 1'
                               }
        }
      }
    }
    stage('sonarqube') {
      steps {
      logstash {
              build 'new1 sonar'
              echo 'sonarqube'
       }
      }
    }
    stage('gate') {
      steps {
      logstash {
        build 'new1gate'
        echo 'sonar gate'
       }
      }
    }
 }

 post {
         always {
              logstashSend failBuild: true, maxLines: 1000
              }

  }
}


