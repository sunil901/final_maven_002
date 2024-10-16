pipeline {
	agent {label 'Build_Maven_server'}
	triggers {
        pollSCM('') //Empty quotes tells it to build on a push
    }
	stages {
	    stage ("1. Git repo") {
	        steps {
	            git branch: 'proj_test', url: 'https://github.com/sunil901/final_maven_002.git'
	        }
	    }
		stage ("2. Build the package") {
			steps {
				sh "mvn clean install"
			}
		}
		stage ("3. Copy the package to S3") {
			steps {
				sh "aws s3 cp target/helloproj-002.war s3://udemo-s3b1"
			}
		}
		
	}
}
