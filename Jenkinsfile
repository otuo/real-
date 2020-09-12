pipeline {
    agent {
          label 'master'
	  }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World Test'
		sh 'mkdir Devops'
		sh 'cat /etc/os-release'
            }
        }
	stage ('Test') {
	  steps {
	    sh 'touch file.txt'
	   }
	}
        stage('DeployToStaging') {
            when {
                branch 'master'
            }
            
        stage('DeployToProduction') {
            when {
                branch 'master'
            }
            steps {
                input 'Does the staging environment look OK?'
                milestone(1)
                withCredentials([sshUserPrivateKey(credentialsId: 'new-ssh', keyFileVariable: 'test', passphraseVariable: 'password', usernameVariable: 'username')]) {
			sh 'ls -al'
		}                 
		   {
                      sshPublisher(
                        failOnError: true,
                        continueOnError: false,
                        publishers: [
                            sshPublisherDesc(
                                sshCredentials: [
                                    username: "$USERNAME"
					]
                               )
                           ]
	             )
		   }
	    }
