pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M398"
    }

    stages {
        stage('Echo Version'){
            steps{
                sh "echo Print Maven Version"
                sh 'which java'
                sh 'java -version'
                sh 'javac -version'
                sh 'mvn -v'
            }
        }
        stage('Build'){
            steps{
                // Get some code from a GH repo
                //git 'https://github.com/sidd-harth/jenkins-hello-world.git'
                git branch: 'main', url: 'https://github.com/Reprak11/jenkins-hello-world.git'
                
                // Run Maven Package CMD
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage('Unit Test'){
            steps{
                sh "mvn test"
            }
        }
    }
}