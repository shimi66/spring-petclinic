pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh '''mvn clean install

'''
      }
    }

    stage('scan') {
      steps {
        sh 'mvn sonar:sonar -Dsonar.login=sqa_940a9352beea22be11c089e4b9016f27af588a18'
      }
    }

    stage('Deploy') {
      steps {
        sh 'mvn spring-boot:run'
      }
    }

  }
}