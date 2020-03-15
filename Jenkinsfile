pipeline {
   agent any

   tools {
      // Install the Maven version configured as "M3" and add it to the path.
      maven "MavenDefault"
   }

   stages {
      stage('Prepare') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/naimadswdn/simpleMavenjob.git'
                }
         }
      stage('Build') {
          steps {
            sh "mvn -Dmaven.test.failure.ignore=true clean package"
                }
          post {
            success {
               junit '**/target/surefire-reports/TEST-*.xml'
               archiveArtifacts 'target/*.jar'
            } }
            }
   }
}
