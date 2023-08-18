	
	node{
	  
	  echo "Jenkins home directory is: ${env.JENKINS_HOME}"
    	echo "job name is: ${env.JOB_NAME}"
	 
	  properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
	 	
	 	
	 	def mavenHome = tool name: 'maven3.9.3'
	 	
	stage('checkoutcode'){
	git branch: 'development', credentialsId: '91eb573b-c972-456f-ab53-87aaa248b4d3',
	url: 'https://github.com/devops-batchs/maven-web-application.git'
	}
	stage('build'){
	sh "${mavenHome}/bin/mvn clean package"
	}
	/*
	stage('executesonarqubereport'){
	 sh "${mavenHome}/bin/mvn clean sonar:sonar" 
	}
	
	 stage('uploadartifactsintonexus'){
	   sh "${mavenHome}/bin/mvn clean deploy"
	 }
	
	    stage('tomcatdeploy'){
	sshagent(['2c555692-e53e-45da-a8b7-e9e7ee4d0599']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.110.171.101:/opt/apache-tomcat-9.0.76/webapps/"
   }
   }
  */
   }
	
