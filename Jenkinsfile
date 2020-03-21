pipeline {
  agent any
  stages {
    stage('Stage 1') {
      steps {
        echo 'This is Step 1'
      }
    }
	stage('Set gitlog variable') {
      steps {
			Script {
				gitlogs = sh(returnStdout: true, script: 'git log -3 --format="%ad | %an | $s"  --date=relative')
		}
      }
    }
	stage('Notify on Slack') {
      steps {
        slackSend colour: '#0000FF', message: "Branch  - '${env.BRANCH_NAME}' Last 3 commits \n\n *===Changes_are===* | *===Author===* | *===Commits===* \n ${gitlogs}"
      }
    }
  }
}