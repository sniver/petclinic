pipeline{
    agent any
    stages{
        stage("build & SonarQube analysis") {
			steps {
			  withSonarQubeEnv('mySonarQube') {
				sh './mvnw clean package sonar:sonar'
			  }
			}
		}
    }
}