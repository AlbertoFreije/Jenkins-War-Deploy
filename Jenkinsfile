pipeline {
    agent any
    tools { 
        maven 'Maven 3.3.9' 
        jdk 'jdk8' 
    }
    stages {
          stage ('Build') {
            steps {
                sh "mvn clean package"
                sh "mv target/*.war target/myweb.war"
            } 
          }

          stage("deploy-Tomcat"){
            steps{
                script{
                    deploy adapters: [tomcat9(credentialsId: 'war-deployer', path: '', url: 'http://192.168.56.10:8081')], contextPath: 'webapp', war: '**/*.war'
                }
                     
            }
            
            }
    
    }
}
