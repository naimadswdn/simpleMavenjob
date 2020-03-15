pipeline {
   agent any

   tools {
      maven "MavenDefault"
   }

   stages {
      stage('Prepare') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/naimadswdn/simpleMavenjob.git'
                }
         }

      stage('Verify') {
                steps {
                    fileExists 'pom.xml'
                    fileExists 'Jenkinsfile'
                      }
                        }

      stage('Build') {
          steps {
            sh "mvn -Dmaven.test.failure.ignore=true clean package"
                }
          post {
            success {
               archiveArtifacts 'target/*.jar'
               input 'Do you want to get tests report?'
               junit '**/target/surefire-reports/TEST-*.xml'
            } 
          }
        }
   }
}
