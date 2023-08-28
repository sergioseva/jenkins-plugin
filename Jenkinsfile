pipeline {
    agent any

    tools {
        maven 'maven 3.9.4'
        jdk 'jdk8'
        git 'Default'
    }

    stages {
         stage ('Build') {
           steps {
             git branch: "main", url: 'https://github.com/sergioseva/jenkins-plugin.git'
             sh 'mvn clean install'
           }
           //post {
           //  success {
           //    junit 'target/surefire-reports/**/*.xml'
           //  }
           //}
         }

      stage('Policy Eval') {
        nexusPolicyEvaluation iqApplication: selectedApplication('5'), iqStage: 'build', iqScanPatterns: [[scanPattern: 'pom.xml'],[scanPattern: '**/*.jar']]
      }
    }
}