
//def ReleaseDir = "c:\inetpub\wwwroot"
pipeline {
			agent any
			stages {
				stage('Source'){
					steps{
						checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '49ffb0e5-9260-42e9-830a-02cdf30b134d', url: 'https://github.com/khion/EF-Samples/blob/master/EF%20Samples/TPT.sln']]])
					}
				}
				stage('Build') {
    					steps {
    					    bat "\"${tool 'MSBuild'}\" TPT.sln /p:DeployOnBuild=true /p:DeployDefaultTarget=WebPublish /p:WebPublishMethod=FileSystem /p:SkipInvalidConfigurations=true /t:build /p:Configuration=Release /p:Platform=\"Any CPU\" /p:DeleteExistingFiles=True /p:publishUrl=c:\\inetpub\\wwwroot"
    					}
				}
			}
}
