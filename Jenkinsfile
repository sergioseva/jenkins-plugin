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
             git branch: "experiment", url: 'https://github.com/sergioseva/jenkins-plugin.git'
             sh 'mvn clean install'
           }
           post {
             success {
               junit 'target/surefire-reports/**/*.xml'
             }
           }
         }

        stage('Policy') {
            steps {
                nexusPolicyEvaluation advancedProperties: '', enableDebugLogging: true,
                    failBuildOnNetworkError: false, iqApplication: selectedApplication('5'),
                    iqScanPatterns: [[]], iqStage: 'build',
                    jobCredentialsId: ''
            }
        }
    }
}