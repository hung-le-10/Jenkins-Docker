pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker hub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/hung-le-10/Jenkins-Docker.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t hungle11/docker:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push hungle11/docker:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
