pipeline {
    agent any
    stages {
        stage('Deps') {
		steps {
			sh 'make deps'
			}
		}	
	stage('Test') {
            steps {
	                sh 'make test_xunit || true'
			step([$class: 'XUnitBuilder',
				thresholds: [
					[$class: 'SkippedThreshold', failureThreshold: '0'],
					[$class: 'FailedThreshold', failureThreshold: '1']],
					tool: [[$class: 'JUnitType', pattern: 'test_results.xml']]])
        	}
		}
        }
    }
