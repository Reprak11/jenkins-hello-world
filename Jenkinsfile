pipeline {
  agent any
  stages {
    stage('Echo Version') {
      steps {
        sh 'echo Print Maven Version'
        sh 'which java'
        sh 'java -version'
        sh 'javac -version'
        sh 'mvn -v'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean package -DskipTests=true'
        archiveArtifacts 'target/hello-demo-*.jar'
      }
    }

    stage('Unit Test') {
      steps {
        script {
          for (int i=0; i < 10; i++){
            echo "${i + 1}"
            sleep 1
          }
        }

        sh 'mvn test'
        junit(testResults: 'target/surefire-reports/TEST-*.xml', keepTestNames: true, keepProperties: true)
      }
    }

  }
  tools {
    maven 'M398'
  }
}