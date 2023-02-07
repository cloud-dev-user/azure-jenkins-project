pipeline{
       agent {
       label 'azure-vm'
           }
	   stages{
	    stage("checkout my code"){
		   steps{
		   git 'https://github.com/cloud-dev-user/azure-jenkins-project.git'
		     } 
	       
           }
		   stage("List my files"){
		   steps{
		     sh 'ls -ltr'
			 }
		   }
        }
}
