node
 {
     def mavenHome = tool name: "maven3.8.1"
     
      properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '5', numToKeepStr: '')), pipelineTriggers([pollSCM('* * * * *')])])
     
     
     stage('CheckoutCode')
     {
         git branch: 'development', credentialsId: '245f6c28-dc09-49bf-80bf-442355c90c6f', url: 'https://github.com/sureshtechy09/maven-web-application.git'
     }
     
     stage('Build')
     {
         sh "${mavenHome}/bin/mvn clean package"
     }
     /* 
     stage('Eexcute Sonarqube Report')
     {
         sh "${mavenHome}/bin/mvn sonar:sonar"
     }
     
     
     stage('Upload Artifacts into Nexus')
     {
         sh "${mavenHome}/bin/mvn deploy"
     }
     
     stage('Deploy application into Tomcat')
     {
         sshagent(['a479e6bf-6b13-4309-8791-0a2438233eac']) {
         sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@54.166.70.228:/opt/apache-tomcat-9.0.58/webapps/"
         }
     } 
     */
     stage('send email')
     {
         emailext body: '''build over..

         Regards,
         Suresh technologies''', subject: 'build over', to: 'sureshaws03@gmail.com'
     }
    
 }     
    
