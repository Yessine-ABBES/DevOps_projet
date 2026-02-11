pipeline {
    agent any
 
    tools {
        maven 'MAVEN_HOME'
    }
 
    stages {
        stage('Compile & Test') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }
    }
}
