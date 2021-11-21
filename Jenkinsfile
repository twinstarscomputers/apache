pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-madhan')
		
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t sm0961/alpha:v1 .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push sm0961/alpha:v1'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
