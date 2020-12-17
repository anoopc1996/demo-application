pipeline {
    agent any
        tools {
            maven 'MAVEN_HOME'
            jdk 'JAVA_HOME'
        }
    stages {
        stage ('Build') {
            steps {
                echo "Building Project"
                bat '''
                mvn clean package install
                '''
            }
        }
        stage('Test') {
            steps {
                bat '''
                 mvn -B verify
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy"
                deploy adapters: [tomcat9(credentialsId: 'da97d4ce-773b-4f01-aa12-15cf2cd19b40', path: '', url: 'http://localhost:8081')], contextPath: 'DemoApplication', war: '**/*.war'
            }
        }
    }
}
