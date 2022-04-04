/* groovylint-disable-next-line CompileStatic */
pipeline {
    agent any
    triggers { pollSCM('* * * * *') }
    stages {
        //implicit checkout stage

        stage('Build') {
            steps {
                powershell './mvnw clean package'
            }
        }
    }
    post {
        always {
            junit '/target/surefire-reports/*.xml'
            archivedArtifacts 'target/*.jar'
        }
    }
}
