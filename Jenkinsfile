pipeline{
    agent any
    stages{
    	stage("Clone"){
		steps{
      	    git credentialsId: 'GIT_HUB_SRK', url: 'https://github.com/ramakrishna8254/new-nodejs-app-cloud4c.git'
        }
	}
        stage("Sonarqube Analysis"){
		steps{
          	nodejs(nodeJSInstallationName: 'nodejs16.19.0'){
        		sh "npm install"
			withSonarQubeEnv('sonarserver'){
				sh "npm install --save-dev mocha chai"
				sh "npm run test"
				sh "npm run coverage-lcov"
				sh "npm install sonar-scanner"
				sh "npm run sonar"
				sh "nohup npm start &"
			}
		}
}
}
}
}
