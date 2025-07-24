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
        stage('Debug WAR') {
            steps {
                sh 'find $PWD -name "*.war"'
            }
        }
        stage('Deploy to Tomcat server') {
            steps {
                deploy adapters: [tomcat9(
                    credentialsId: 'tompass', 
                    path: '', 
                    url: 'http://13.216.238.92:8080/'
                )], 
                contextPath: 'myapp', 
                war: 'SampleWebApp/target/*.war'
            }
        }
    }
}



// pipeline {
//     agent any

//     stages {
//         stage('Build') {
//             steps {
//                 sh 'cd SampleWebApp && mvn clean package'
//             }
//         }
//         stage('Test') {
//             steps {
//                 sh 'cd SampleWebApp && mvn test'
//             }
//         }        
        
//         stage('Deploy to Tomcat server') {
//             steps {
//                 deploy adapters: [tomcat9(credentialsId: 'tompass', path: '', url: 'http://13.216.238.92:8080/')], contextPath: 'myapp', war: '**/*.war'
//                 //deploy adapters: [tomcat9(credentialsId: 'tompass', path: '', url: 'http://54.82.61.200:8080/')], contextPath: 'myapp', war: '**/*.war'
//             }
//         }
//     }
// }