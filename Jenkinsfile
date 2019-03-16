node {

	stage('SCM'){
		//git clone
		git 'https://github.com/openmrs/openmrs-core.git'
	}

	//stage ('build the package'){
		//mvn package
		//sh 'mvn package'
	//}

	stage('build & SonarQube Scan') {
    withSonarQubeEnv('My SonarQube Server') {
      sh 'mvn clean package sonar:sonar'
    } // SonarQube taskId is automatically attached to the pipeline context
  }

	stage('SonarQube analysis') {
    // performing sonarqube analysis with "withSonarQubeENV(<Name of Server configured in Jenkins>)"
    withSonarQubeEnv('SONAR-6.7.4') {
      // requires SonarQube Scanner for Maven 3.2+
      sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar'
    }
  }
	
	//stage ('archival'){
		// archiving artifacts
	//	archive 'target/*.jar'
	//}
}