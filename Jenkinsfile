pipeline { 
    agent any  
	    tools{
        
			maven 'LocalMaven'
			 }
		stages { 
			stage('checkout') { 
				steps { 
					checkout([$class: 'SubversionSCM', additionalCredentials: [], excludedCommitMessages: '', excludedRegions: '', excludedRevprop: '', excludedUsers: '', filterChangelog: false, ignoreDirPropChanges: false, includedRegions: '', locations: [[cancelProcessOnExternalsFail: true, credentialsId: 'f8ff7cc9-9385-4b36-b928-c1aa97b3866a', depthOption: 'infinity', ignoreExternalsOption: true, local: '.', remote: 'http://cbsasvnserver1/apps/ssas/branches/experimental/Gurleen/TestCICD']], quietOperation: true, workspaceUpdater: [$class: 'UpdateUpdater']])
					}
			stage('build'){
				steps{
					bat 'mvn clean package'
					 }
				}
			stage('codequality'){
				steps{
					withSonarQubeEnv('SonarQubeDefault'){
					bat 'mvn sonar:sonar -Dsonar.login=bd918029ffdfc38736adbc0515bc2f0b4e8e4de9'}
                     		     }
					    }

		}
	}