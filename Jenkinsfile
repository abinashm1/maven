node('master') {
    stage('ContinuousDownload') {
    git 'https://github.com/abinashm1/maven.git'
    }
    stage('ContinuousBuild'){
    sh label: '', script: 'mvn package'
    }
    stage('ContinuousDeployment'){
    sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.42.3:/var/lib/tomcat8/webapps/testapp.war'
    }
    stage('ContinuousTesting'){
    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('ContinuousDelivery'){
    sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.39.254:/var/lib/tomcat8/webapps/prodapp.war' 
    }
    
    
}
