pipeline {
    agent any

    tools {
        maven 'maven'
        jdk 'jdk'
        git 'git'
    }

    stages {
        // stage ('Build') {
        //   steps {
        //     git branch: "experiment", url: 'https://github.com/koraytugay/groovyship.git'
        //     sh 'mvn clean install'
        //   }
        //   post {
        //     success {
        //       junit 'target/surefire-reports/**/*.xml'
        //     }
        //   }
        // }

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