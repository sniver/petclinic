pipeline{
    agent any
    stages{
        stage("build & SonarQube analysis") {
			steps {
			  withSonarQubeEnv('My SonarQube Server') {
				sh './mvnw clean package sonar:sonar'
			  }
			}
		}
    }
}