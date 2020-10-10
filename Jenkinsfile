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
	    sh 'touch test.txt'
	   }
	}     
        stage('Deploy') {
		steps {
		sh 'uname'
	      
	}
    }
  }
}
