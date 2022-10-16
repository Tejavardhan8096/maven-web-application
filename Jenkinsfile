node{
    
    def mavenHome = tool name: "Maven3.8.5"    
    
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '3', daysToKeepStr: '', numToKeepStr: '3')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pollSCM('* * * * *')])])
    
    stage('checkout code')
    {
      git branch: 'development', credentialsId: '1815bb6e-b614-45a6-a00e-71791d8629ec', url: 'https://github.com/Tejavardhan8096/maven-web-application.git'  
    }
    stage('Build')
    {
        sh "${mavenHome}/bin/mvn clean package"
    }
    stage('Execute SonarQube')
    {
        sh "${mavenHome}/bin/mvn sonar:sonar"
    }
    /*
    stage('Upload Artfcts into Nexus')
    {
        sh "${mavenHome}/bin/mvn deploy"
    }
    stage('Deploy into Tomcatserver')
    {
        sshagent(['dea3d11f-ab3c-48a7-8c43-f26ba5a05622']) {
            sh "scp -o strictHostkeychecking=no target/maven-web-application.war  ec2-user@3.6.93.86:/opt/apache-tomcat-9.0.67/webapps"
    }
    }
    */
}
