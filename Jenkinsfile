pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-madhan')
		
	}

	stages {

		stage('Build') {

			steps {
				sh 'chmod 777 httpd-foreground'
				sh 'docker build -t sm0961/alpha:$tag .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push sm0961/alpha:$tag'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
