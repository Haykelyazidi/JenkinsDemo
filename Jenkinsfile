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
                script{
                sh 'mvn clean test '
                testNG reportFilenamePattern: 'target/surefire-reports/testng-results.xml'
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'target/surefire-reports/Extend*.html', reportName: 'HTML HAYKEL Report', reportTitles: '', useWrapperFileDirectly: true])        }}
    }
}
