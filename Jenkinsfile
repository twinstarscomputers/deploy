pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-madhan')
		key = 'BUILD_VERSION'
		
	}
	stages {
	         
		 stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		 }
		
	

		  stage('Deploy') {

			steps {
				sh 'docker rm -f apache_deploy'
				sh 'docker run -d --name apache_deploy -p 8082:80 -v /var/run/docker.sock:/var/run/docker.sock  sm0961/alpha:$tag'
			}
		 }
      
	}
	

	post {
		always {
			sh 'docker logout'
		}
	}
}
