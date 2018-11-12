pipeline {
 agent {

      node {
      deleteDir()

      stage ‘build’
      sh ”’#!/bin/bash
      echo “This is the pipeline test”
      ”’
      logstashSend failBuild: true, maxLines: 1000
      }
 }
 stages {
   stage('checkout') {
     steps {
       git(url: 'https://github.com/kshitizsh12/Simple.git', branch: 'master', changelog: true, credentialsId: '10sharma10', poll: true)
     }
   }
   stage('build') {
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


