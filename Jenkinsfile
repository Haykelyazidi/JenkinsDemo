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
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'target/surefire-reports/reporthay*.html', reportName: 'HTML HAYKEL Report', reportTitles: '', useWrapperFileDirectly: true])
            }
        }
    }
}
