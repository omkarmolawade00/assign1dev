pipeline {
    agent any 
    tools {
       
        maven 'M3'
     

    }
    stages {
        stage('build && SonarQube analysis') {
            steps {
                withSonarQubeEnv('Sonar-Server') {
                    // Optionally use a Maven environment you've configured already
                    withMaven(maven:'Maven-3.8.7') {
                        bat 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
        stage("Quality Gate") {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                    // true = set pipeline to UNSTABLE, false = don't
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}
