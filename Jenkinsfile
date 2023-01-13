pipeline {
    agent any

 

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
       
    }

 

    stages {
        stage('Build') {
            steps {
                
                 
                // Get some code from a GitHub repository
                git 'https://github.com/omkarmolawade00/assign1dev.git'

                dir("C:/ProgramData/Jenkins/.jenkins/workspace/assign1demo_master")  {
                 bat ' '
                }

                // Run Maven on a Unix agent.
                bat "mvn -Dmaven.test.failure.ignore=true clean package"

 

                // To run Maven on a Windows agent, use
                //bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
    

 

     post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
              
        always {
            junit(
                allowEmptyResults: true,
                testResults: '*/test-reports/.xml'
          )
      
   }
    }

    }
}
