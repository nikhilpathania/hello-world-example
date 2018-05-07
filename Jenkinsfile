pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Build') {
      steps {
        withMaven(maven: 'Maven 3.3.3') {
          sh 'mvn clean install'
        }

        withMaven(maven: 'Maven 3.3.3')
        sh 'mvn -Dmaven.test.failure.ignore clean package'
      }
    }
    stage('Results') {
      steps {
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts 'target/*.jar'
      }
    }
  }
}
