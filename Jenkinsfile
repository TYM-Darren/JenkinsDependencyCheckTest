pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git url: 'https://github.com/TYM-Darren/JenkinsDependencyCheckTest.git', branch: 'master'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP Dependency-Check Vuln'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
