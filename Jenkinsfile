node('built-in') 
{
    stage('ContinuousDownload') 
    {
        git 'https://github.com/PrasadGit002/maven1.git'
    }
    stage('ContinuousBuild') 
    {
        sh 'mvn package'
    }
     stage('ContinuousDeployment') 
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/scriptedpl1/webapp/target/webapp.war ubuntu@172.31.0.121:/var/lib/tomcat9/webapps/testapp.war'
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
