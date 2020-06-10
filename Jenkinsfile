pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        sh './gradlew build'
      }
    }

    stage('Test') {
      steps {
        echo 'Testing..'
        sh './gradlew test'
        sh './gradlew check'
      }
    }

    stage('Analyze') {
      steps {
        echo 'Sonarqube...'
        sh './gradlew sonarqube -Dsonar.host.url=http://sonarqube:9000'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }

  }
  post {
    always {
      archiveArtifacts(artifacts: 'build/libs/**/*.jar', fingerprint: true)
    }

  }
}