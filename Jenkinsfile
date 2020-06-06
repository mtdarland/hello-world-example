pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Build') {
      steps {
        withMaven(maven: 'M3') {
          sh '''man clean install
'''
        }

      }
    }

    stage('Report') {
      steps {
        junit '**/target/surefire-reports/TEST-*.xml'
      }
    }

    stage('Archive') {
      steps {
        archiveArtifacts 'target/*.jar'
      }
    }

  }
}