pipeline {
 agent any
  options {
     timestamps()
  }
  stages {
    stage('checkout') {
      steps {
        git(url: 'https://github.com/kshitizsh12/Simple.git', branch: 'master', changelog: true, credentialsId: '10sharma10', poll: true)
       }
    }
    stage('build') {
      options {
                      timestamps()
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

   post {
         always {
              logstashSend failBuild: true, maxLines: 1000
              }

    }
}
