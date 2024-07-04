pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/CJNandu/mywar.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'b7dd447d-e90e-41de-8aed-5f01b63f3794', path: '', url: 'http://172.31.80.58:8080')], contextPath: 'testapp2', war: '**/*.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                
                sh 'java -jar /var/lib/jenkins/workspace/dev2/testing.jar'
            }
        }
        stage('ContinuousDelivary')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'b7dd447d-e90e-41de-8aed-5f01b63f3794', path: '', url: 'http://172.31.88.198:8080')], contextPath: 'prodapp2', war: '**/*.war'
            }
        }
    }
}
