pipeline {
   agent { 
        
           label "docker" 
           
           
           }
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
                bat 'mvn clean compile '
            }
        }
      stage('test') {
            steps {
                script{
                bat 'mvn clean test -Dbrowser=localchrome'
                testNG reportFilenamePattern: 'target/surefire-reports/testng-results.xml'
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'target/surefire-reports/Extend*.html', reportName: 'HTML HAYKEL Report', reportTitles: '', useWrapperFileDirectly: true])        }}
    }
}
}
