pipeline {
    agent {
          label 'master'
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
            when {
                branch 'master'
            }
		steps {
                withCredentials([usernamePassword(credentialsId: 'user-centos', passwordVariable: 'upass', usernameVariable: 'uname')]) {
                sh 'scp -r ~/team centos@ec2-34-216-195-161.us-west-2.compute.amazonaws.com:~/'
	        sshCredentials: [
                                    username: "$uname",
                                    encryptedPassphrase: "$upass"
                                ]
                }
	    }
	  }
      }
