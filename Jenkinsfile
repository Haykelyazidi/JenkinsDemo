pipeline {
    agent any
     tools {
        maven "mvn"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

    
        stage('Compile') {
            steps {
                sh 'mvn clean compile '
            }
        }
      stage('test') {
            steps {
                sh 'mvn clean test '
                testNG reportFilenamePattern: '**/testng.xml'
            }
        }
    }
}
