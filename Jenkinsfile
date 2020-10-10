pipeline {
    agent {
          label 'slave123'
	  }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World Test'
		sh 'cat /etc/os-release'
            }
        }
	stage ('Test') {
	  steps {
	    sh 'touch file.txt'
	   }
	}     
        stage('Deploy') {
		steps {
                
	        sh 'ssh ec2-user@ec2-18-236-239-105.us-west-2.compute.amazonaws.com'
		sh 'uname'
	      
	}
    }
  }
}
