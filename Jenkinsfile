pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/ShaunVSIT/JenkinsDependencyCheckTest'
            }
        }

		stage('OWASP Dependency-Check Vulnerabilities') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Default'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}