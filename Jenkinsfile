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
                node {
                    try { 
                            build 'new 1'
                            echo 'project build'
                            currentBuild.result = 'SUCCESS'
                         } catch (Exception err) {
                            currentBuild.result = 'FAILURE'
                           }
                    echo "RESULT: ${currentBuild.result}"
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


