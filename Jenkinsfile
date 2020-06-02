pipeline {
    agent any
    stages {
        stage('Compile') {
            steps {
                sh '/usr/local/bin/mvn clean package -DskipTests=true'
            }
        }
        stage('Unit Tests') {
            steps {
                sh '/usr/local/bin/mvn surefire:test'
            }
        }
         stage('Integration Tests') {
            steps {
                sh '/usr/local/bin/mvn failsafe:integration-test'
            }
        }
    }
    post {
        always {
            junit 'target/surefire-reports/TEST-*.xml'
        }
       // failure {
            //mail to: 'kiwaczki@gmail.com', subject: 'The Pipeline failed :(', body:'The Pipeline failed :('
       // }
    }
}
