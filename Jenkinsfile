pipeline{
    agent any
    stages{
        stage("build"){
            steps{
                sh "./mvnw package"
            }
        }
        
        stage("capture"){
            steps{
                archiveArtifacts artifacts: '**/target/*.jar', followSymlinks: false
                jacoco()
                junit stdioRetention: '', testResults: '**/target/surefire-reports/TEST*.xml'
            }
        }
    }
    
    post{
        always{
            emailext body: "${env.BUILD_URL}\n${currentBuild.absoluteUrl}", 
            to: 'mahdy@foo.bar',
            recipientProviders: [previous()], 
            subject: "${currentBuild.currentResult} : Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]"
        }
    }
}