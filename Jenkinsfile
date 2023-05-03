node('built-in') 
{
    stage('ContinuousDownload') 
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild') 
    {
        sh 'mvn package'
    }
     stage('ContinuousDeployment') 
    {
        deploy adapters: [tomcat9(credentialsId: '23b397e2-dbd8-41f1-b9d7-b6eeb4f8374e', path: '', url: 'http://172.31.0.121:8080')], contextPath: 'testapp', war: '**/*.war'
    }    
     stage('ContinuousTesting') 
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/DevPipe/testing.jar'
    }
    stage('ContinuousDelivery') 
    {
        input message: 'Need approval', submitter: 'srinivas'
        deploy adapters: [tomcat9(credentialsId: '10564694-bdfc-4504-8514-e30f8de2b82d', path: '', url: 'http://172.31.6.150:8080')], contextPath: 'prodapp', war: '**/*.war'
    }

}
