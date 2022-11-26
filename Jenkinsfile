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
      parallel {
        stage('Deploy') {
          steps {
            sh 'mvn spring-boot:run'
            sleep(time: 2, unit: 'MINUTES')
            sh '^C'
            cleanWs()
          }
        }

        stage('Ansible Deploy') {
          steps {
            sh 'ping 172.21.177.25'
          }
        }

      }
    }

  }
}