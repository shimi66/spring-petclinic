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
        sh 'mvn sonar:sonar -Dsonar.login=sqa_4c615c8b416aa2424b29a852a0db1f73829c3aeb'
      }
    }

    stage('Deploy') {
      steps {
        sh 'mvn spring-boot:run'
      }
    }

  }
}