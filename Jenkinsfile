pipeline {
    agent {
          label 'master'
	  }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World Test'
		sh 'ls'
            }
        }
        stage(gitcheckout) {
            steps {
                echo 'gitcheckout new'
            }
        }
    }
}
