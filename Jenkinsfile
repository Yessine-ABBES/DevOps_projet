pipeline {
    agent any
    
  environment {
        JAVA_HOME = "/usr/lib/jvm/java-21-openjdk-amd64"
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }
    
    tools {
        maven 'MAVEN_HOME'
    }
 
    stages {
        stage('Compile & Test') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }
        stage('SONARQUBE') {
    environment {
        SONAR_HOST_URL='http://192.168.50.4:9000/'
        SONAR_AUTH_TOKEN= credentials('sonarqube')
    }
    steps {
        sh 'mvn sonar:sonar -Dsonar.projectKey=devops_git -Dsonar.host.url=$SONAR_HOST_URL -Dsonar.token=$SONAR_AUTH_TOKEN'
    }
}
    }
}
