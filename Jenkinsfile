pipeline {
    agent {
          label 'master'
	  }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World Test'
		sh 'mkdir test'
		sh 'ls -al'
            }
        }
	stage ('Test') {
	  steps {
	    sh 'touch file.txt'
	   }
	}
        stage(gitcheckout) {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/otuo/real-.git']]])
            }
        }
    }
}
