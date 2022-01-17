pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker hub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/shazforiot/nodeapp_test.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t hungle11/jenkins-docker:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push hungle11/jenkins-docker:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
