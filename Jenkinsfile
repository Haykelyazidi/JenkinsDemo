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
              cleanWs()
              checkout scm
            }
        }

    
        stage('Compile') {
            steps {
                bat script:  'mvn clean compile '
            }
        }
      stage('test') {
            steps {
                script{
                bat script:  'mvn clean test -Dbrowser=localchrome'
                testNG reportFilenamePattern: 'target/surefire-reports/testng-results.xml'
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'target/surefire-reports/emailable-report.html', reportName: 'HTML HAYKEL Report', reportTitles: '', useWrapperFileDirectly: true])        }}
    }
}
}
