pipeline{
    agent any
    stages{
        stage('Continuous Download'){
            steps{
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        
        stage('Continuous Build'){
            steps{
                sh 'mvn package'
            }
        }
        
        stage('Continuous Deployment'){
            steps{
                deploy adapters: [tomcat9(credentialsId: '2fa6f45b-7022-4cee-905c-f1a68100877d', path: '', url: 'http://172.31.36.101:8080')], 
                contextPath: 'test1', war: '**/*.war'
            }
        }
        
        stage('Continuous Testing'){
            steps{
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        
        stage('Continuous Delievery'){
            steps{
                deploy adapters: [tomcat9(credentialsId: '2fa6f45b-7022-4cee-905c-f1a68100877d', path: '', url: 'http://172.31.35.204:8080')], 
                contextPath: 'pod1', war: '**/*.war'
            }
        }
    }
}
