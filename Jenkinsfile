pipeline {
  agent any

  environment {
    JIRA_SITE = 'kine-jira' // Your configured Jira Site ID
  }

  stages {
    stage('Notify Build Status') {
      steps {
        script {
          jiraSendBuildInfo(
            issueKeys: ['KC-7944'], // Can be dynamically resolved using JiraIssueKeyHelper
            pipelineId: env.BUILD_ID,
            pipelineDisplayName: env.JOB_NAME,
            state: 'successful'
          )
        }
      }
    }

    stage('Deploy') {
      steps {
        echo '🚀 Deploying the app...'
        // Your deployment steps
      }
    }

    stage('Notify Deployment') {
      steps {
        script {
          jiraSendDeploymentInfo(
            environmentId: 'dev',         // e.g., dev, staging, prod
            environmentName: 'Development',
            environmentType: 'development', // development | staging | production
            issueKeys: ['KC-7944'],
            deploymentState: 'successful', // or 'failed'
            pipelineId: env.BUILD_ID,
            pipelineDisplayName: env.JOB_NAME
          )
        }
      }
    }
  }
}