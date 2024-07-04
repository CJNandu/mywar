node('built-in') 
{
    stage('Continuous Download') 
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('Continuous Build') 
    {
        sh 'mvn package'
    }
    stage('Continuous Deployment')
    {
        deploy adapters: [tomcat9(credentialsId: 'b7dd447d-e90e-41de-8aed-5f01b63f3794', path: '', url: 'http://172.31.80.58:8080')], contextPath: 'testapp1', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        
        sh 'java -jar /var/lib/jenkins/workspace/dev1/testing.jar'
    }
    stage('ContinuousDelivary')
    {
        deploy adapters: [tomcat9(credentialsId: 'b7dd447d-e90e-41de-8aed-5f01b63f3794', path: '', url: 'http://172.31.88.198:8080')], contextPath: 'prodapp1', war: '**/*.war'
    }
    
}
