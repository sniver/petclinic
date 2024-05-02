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
		
		stage("Quality Gate") {
			steps {
				timeout(time: 1, unit: 'HOURS') {
					waitForQualityGate abortPipeline: true
				}
			}
		}
    }
}