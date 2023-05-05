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
     sh 'scp /home/ubuntu/.jenkins/workspace/scriptedpl1/webapp/target/webapp.war ubuntu@172.31.6.150:/var/lib/tomcat9/webapps/prod.war'  
    }

}
