pipeline {
  agent any

  environment {
    JIRA_SITE = 'https://kine.atlassian.ne' // Same as configured in Jenkins
  }

  stages {
    stage('Build') {
      steps {
        echo 'Building...'
        // Build steps here
      }
    }

    stage('Notify Jira') {
      steps {
        script {
          jiraSendBuildInfo()
        }
      }
    }
  }
}
