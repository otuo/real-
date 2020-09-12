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
		steps {
                withCredentials([usernamePassword(credentialsId: 'user-centos', passwordVariable: 'upass', usernameVariable: 'uname')]) {
	        sshPublisherDesc(
                                sshCredentials: [
                                    username: "$uname",
                                    encryptedPassphrase: "$upass"
                                ], 
                                transfers: [
                                    sshTransfer(
                                        sourceFiles: '~/team',
                                        remoteDirectory: '/tmp',
                                        execCommand: 'ls -al'
                                    )
                                ]
                            )
		      }
	      }
	}
    }
}
