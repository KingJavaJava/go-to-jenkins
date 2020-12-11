pipeline {
	agent any

	environment {
		GO111MODULES = 'on'
	}
	tools {
		go 'go-1.15.6'
	}
	stages {
		stage('Build') {
			steps {
				sh 'go build'
			}
		stage('Testing') {
				environment {
					CODECOV_TOKEN = credentials('CODECOV_TOKEN')
				}
				steps {
					sh 'go test ./... -coverprofile=coverage.txt'
					sh 'curl -s https://codecov.io/bash | bash -s -'
				}
			}
		}
	}
}