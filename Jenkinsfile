pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'cd SampleWebApp && mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'cd SampleWebApp && mvn test'
            }
        }        
        
        stage('Deploy to Tomcat server') {
            steps {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tompass', path: '', url: 'http://54.82.61.200:8080/')], contextPath: 'myapp', war: '"**/*.war"'
                //deploy adapters: [tomcat9(credentialsId: 'tompass', path: '', url: 'http://54.82.61.200:8080/')], contextPath: 'myapp', war: '**/*.war'
            }
        }
    }
}
